% Systems and in Silico Biology
% Saul Pierotti
% \today

# Introduction
* The first part is about machine learning methods, mostly at the theoretical level
	* The practical application of SVM and kernel methods is part of the LB2 project
* In an HMM the objective function (Baum-Welch function) has as parameters the emission and transition probabilities
* The maximum likelihood (a priori) estimate of an HMM is the set of parameters that maximises the probability of the training set given the parameters ($p(D|\theta)$)
* The a posteriori estimate maximises the probability of the parameters given the training data ($p(\theta|D)$)
	* The a posteriori estimate does not use the Baum-Welch function
* The biggest risk in ML is avoiding overfitting

# Neural Networks

## History of Deep Learning
* Deep Learning existed under many names since 1940 (Cybernetics, Connectionism, Deep Learning)
* Interest for Deep Learning experienced 3 peaks, with intervening distrust
* The first wave of interest came in 1940 with the first simple networks
	* At this time the concept was called Cybernetics
	* It disappeared when it was shown that a single-layer perceptron cannot solve the XOR problem
	* This is the time when stochastic gradient descent was developped
* The second wave came in 1980 and lasted until late 1990
	* It arose in the context of cognitive science
	* It lost interest due to inflated expectations
* The current wave arose in 2006, thanks to an influential paper by Hinton for deep-network training
	* At this time the concept was called Connectionism
	* Actually good training algos existed since 1980, but the hardware at the time was not powerful enough to exploit them
* In the past the interest was more in unsupervised learning from small datasets, but now it is on supervised learning on huge datasets

## Linear Classification Models
* Linear classification means finding a line that separates classes of data
* We want to use a line since it is a simple model, and it minimises the risk of overfitting
* A line can be described as $x_1 = ax_2+b$, but this is not the most effcient way
* I can better write a line as $w_1 x_1 + w_2 x_2 + b = 0$, since this is extendable to higher dimensions
* The equation of a plane can thus be written as $w_1 x_1 +w_2 x_2 +w_3 x_3 +b = 0$
* In general I can write the equation for any linear manifold (hyperplane) $\vec{x} \in \mathbb{R}^n$ as
$$\vec{w}\vec{x} + b = 0$$
* In this framework $\vec{w}$ and $b$ are the paramters to be trained
	* This description holds also for support vector machines (SVMs) and neural networks (NNs)
* Mach's bands: perception can be different than the actual signal
	* We can treat a retina neuron as a linear model that given a incident light intensity outputs a voltage proportional to it
	* Suppose that neurons are laterally connected to each other with inhibitory connections
	* The strenght of inhibition of a neuron on other neurons is proportional to the potential of the neuron itself
	* At the intensity boundary the highly active neuron inhibits the less active neuron more than what another less active neuron would do
	* As a consequence, the less active neuron at the boundary is less active than other neurons of the less active region
	* The same is true in reverse: the highly active neuron at the boundary is more active that other highly active neurons
	* This phenomenon of lateral inhibition is actually present in the retina
* Simple elements can engage in complex behaviours when they are widely and specifically connected
	* Knowledge is stored in the topology and in the strenght of the synapses
* A model for an artificial neuron: McCulloch and Pitts
	* A neuron is a computational unit that performs weighted sums of the input signal $\vec{x}$, computing the activation signal
$$ a = \vec{w} \vec{x} - \theta = \sum_{i=1} w_ix_i - \theta$$
	* In this equation $\theta$ is the activation threshold, $\vec{w}$ the weights vector and $\vec{x}$ the inputs vector
	* The activation signal is transformed by a transfer function $g(a)$ to give the output $z$
$$z = g(a)$$

## Transfer Functions
* A trasfer (or activation) function $g(x)$ is a function that given an activation $a$, outputs an output signal $z$ from the neuron such that $z=g(a)$
* Transfer functions can be simply linear functions
$$g(a) = ma$$
* The trasfer function is ideally not linear, in order to allow to model compelx dependencies on the input
	* It is desirable than neurons behave with a all-or-none response type, so the transfer function should be binary
	* With a non-linar function, the same variation in the input can give very different variations in the output, depending on the absolute activation level
* The Heaviside (Oliver Heaviside) is a possible binary activation function
$$ g(a) = \begin{cases}0 & \mbox{if }a < 0 \\ 1 & \mbox{if } a \geq 0\end{cases}$$
	* It returns 0 for negative inputs and 1 for positive inputs
	* This function has the inconvenience of not being continuous, and thus it is not derivable
* A more convenient almost-binary activation function is the sigmoid function
$$g(a)=\frac{1}{1+e^{-a}}$$
* The ReLU function (Rectifying Linear Unit) is continuous but not derivable
$$ g(a) = \begin{cases}0 & \mbox{if }a < 0 \\ a & \mbox{if } a \geq 0\end{cases}$$
	* It is horizontal until 0 and then becomes linear
	* The angular point ($a=0$) is not derivable

## Perceptron
* The topology of the connections among neurons defines the network class
* In feed-forward networks the activation travels only forward
	* There are no connections among neurons of the same level, or with neurons of previous levels
* The simplest NN is the perceptron: an input layer and an output layer with only feed-forward connections
* The output of each output neuron $z_j$ of the perceptron can be expressed in terms of the inputs $\vec{x}$ and the weights $\vec{w}$
$$ z_j = g(\sum_i(w_{ij} x_i) - \theta_j)$$
* I can replace the threshold $\theta$ with a fictitious neuron always activated ($x=1$) which is connetced to the current neuron with a weight $w=-\theta$
$$ z_j = g(\sum_i w_{ij} x_i)$$
$$ z_j = g(\vec{x}\vec{w_j})$$
* I can implement an OR gate with a perceptron with 2 inputs $x_1,x_2$ and 1 output $z_3$
	* I can use a Heaviside transfer function
	* Weights are $w_{13}=w_{23}=0.5$ and the threshold is $\theta_3=0.25$
* With the same topology but different parameters I can implement an AND gate
	* I just change the threshold such that $\theta_3=0.75$
* Also a NOT(1) can be implemented with the same topology
	* I choose $w_{13}=-0.5$, $w_{23}=0.1$, $\theta_3=-0.25$
* The weights $w$ are the trainable parameters of the network
	* Training means optimizing the value of the trainable parameters for a set of know examples
* The non trainable parameters of the network are called hyperparameters
	* In the perceptron these are the number of neurons in the input and output layers
* NNs can be trained from a set of labeled examples (supervised learning)
	* I can start from random values
	* For a given set of parameters $\vec{w}$, I evaluate the output vector $\vec{z}$ for a set of examples (training data) $\vec{x}^{(k)}$
	* I compare the outputs $\vec{z}^{(k)}$ with a set of desired outputs for the training set $\vec{d}^{(k)}$
* I can define an error (or loss) function $E$ that represents how well the output $\vec{z}^{(k)}$ agrees with the desired output $\vec{d}^{(k)}$
	* In this representation $k$ represents the training examples, $i$ the input neuron, and $j$ the output neuron

## Error Functions
* A possible error function is the simple difference
$$ E = \sum_{k,j} (z_j(x^{(k)},w)-d_j^{(k)}) $$
	* This is not a good function since contributions with opposite signs cancel each other
* I can use the absolute values of the differences
$$ E = \sum_{k,j} |z_j(x^{(k)},w)-d_j^{(k)}| $$
	* The absolute value is not derivable, and so it does not allow to calculate a gradient
* It is better to use the square of the error
$$ E = \frac{1}{2}\sum_{k,j} (z_j(x^{(k)},w)-d_j^{(k)})^2 $$
	* The constant factor $\frac{1}{2}$ is useful to simplify a computation later, it does not have a specific meaning
		* It makes the expression more similar the one for kinetic energy
	* This is the most used error function in classical neural networks
* The cross entropy is another possible error function
$$ E = -\frac{1}{m}\sum_{k,j} (d_j^{(k)}\ln{z_j(x^{(k)},w)})$$
	* $m$ is the number of output neurons
* After evaluating my error function, I need to update my parameters accordingly if the error is not below a satisfactory threshold
* I can update the parameters randomly
	* This is used in some approaches, but in general it is not so smart if the parameter space is really large
	* In a perceptron with $n$ input neurons and $m$ output neurons the parameter space is $(n+1)m$ (weights plus the thresholds)
		* I have $nm$ weights and $m$ thresholds

## Gradient
* A gradient is a vector containing all the first order partial derivatives of a function
$$ \nabla f(x)= (\frac{\partial f}{\partial x_1},\frac{\partial f}{\partial x_2},...,\frac{\partial f}{\partial x_n})$$
* The gradient is always perpendicular to the level curves
* Given a function $f(x,y)$, and a level curve $f(x,y)=c$, the gradient is
$$\nabla f = (\frac{\partial f}{\partial x},\frac{\partial f}{\partial y})$$
* If I consider 2 points on the level curve $f(x,y)=c$, that are $(x,y)$ and $(x+\epsilon_x,y+\epsilon_y)$
* For $\epsilon_x,\epsilon_y \to 0$ I notice that
$$f(x+\epsilon_x,y+\epsilon_y)\approx f(x,y) + \epsilon_x \frac{\partial f}{\partial x}|_{(x,y)} + \epsilon_y \frac{\partial f}{\partial y}|_{(x,y)}=f(x,y)+\epsilon^T \nabla f|_{(x,y)}$$
	* The new points tends to approximate the old point plus 2 contributions of magnitude $\epsilon$, in the direction of the partial derivatives with respect to $x$ and to $y$
* Since both points belong to the curve $f(x,y)=c$, I obtain that
$$c \approx c + \epsilon^T \nabla f|_{(x,y)}$$
* This implies that the product of the movent along the curve $\epsilon^T$ and the gradient at that point is 0
$$\epsilon^T \nabla f|_{(x,y)} = 0$$
* Since this product is 0, it means that the gradient is perpendicular to the level curve
* The gradient always points in the direction of maximal increase of $f$

## Training the Perceptron
* The error function is a function
$$ E_{\vec{w},\theta} : \mathbb{R}^{(n+1)m} \to \mathbb{R}$$
	* $n$ is the number of inputs and $m$ the number of outputs
* Training means finding the set of parameters $w$ (which includes $\theta$) that minimizes the error function
* Iterative algorithms are generally adopted,but they do not guarantee to find a global minimum
* If the desired output $d$ is binary we have a classification problem, if it is a real number a regression problem
* Gradient descent finds a LOCAL minimum of a function by always going against the gradient





* A function with 2 to inputs and 1 output can be represented with contour lines
* The gradient evaluated at a point $\vec{w}_0$ is the vector of all the first order partial derivatives evaluated at that point
$$ \nabla f(x)|_{\vec{w}_0}= (\frac{\partial f}{\partial x_1}|_{\vec{w}_0},\frac{\partial f}{\partial x_2}|_{\vec{w}_0},...,\frac{\partial f}{\partial x_n}|_{\vec{w}_0})$$




* The analytical solution of the maxima and minima of the error function is usually not computationally feasible
	* I am in a extremum (or a saddle/flexus) when all the partial derivatives of the error function are 0
	* In order to define a gradient the error function must be derivable
	* Since the error function includes the transfer function, also this must be derivable
	* This approach would be really good since it does not need any inizialization and outputs a set of all the extrema and saddle points/flexuses
	* I could then just subsitute for all of these points and find the global extrema
* I can use gradient descent for updating the parameters
	* I update the parameters in the direction that would lower the error function, given the set of partial derivatives (the gradient!)
	* I can define the new parameter $w_1$ as a function of the old parameter $w_0$
$$ w_1 = w_0 - \eta \frac{\partial E}{\partial w}|w_0$$
	* $\eta$ is the learning rate, a hyperparameter
	* I repeat the process iteratively until $E$ is below a certain acceptable threshold
* The general rule for the steepest descent is that I start from a function $E(\vec{w})$, and from the point $\vec{w}_0$, and I define the next point $\vec{w}_1$ as $\vec{w}_1 = \vec{w}_0 - \eta \nabla E | \vec{w}_0$
* This can be generalised as
$$\vec{w}_{t+1}= \vec{w}_t - \eta \nabla E | \vec{w}_t$$
* Demonstration of orthogonality of gradient to level curves xxx
* An analytical procedure for finding a global extremum of a function is still an open problem
* In order to optimize the choice of learning rate, I can use the second order partial derivatives (Hessian matrix)
* A perceptron performs a mapping $\mathbb{R}^n \to \mathbb{R}^m$
* Given the error function $E$, with transfer function $g(a)=\frac{1}{1+e^{-a}}$
$$ E(\vec{w}) = \frac{1}{2}\sum_{k,j} (z_j(x^{(k)},\vec{w})-d_j^{(k)})^2 $$
* I want to compute the gradient $\nabla E$
* I can compute the derivative of $E$ relative to a specific weight $w_{rs}$ (the weight from input $r$ to output $s$) by scomponing the problem with the chain rule
$$\frac{\partial E}{\partial w_{rs}} = \frac{\partial E}{\partial z_s}\frac{\partial z_s}{\partial w_{rs}}$$
$$= \frac{\partial E}{\partial z_s}\frac{\partial z_s}{\partial a_s}\frac{\partial a_s}{\partial w_{rs}}$$
* I can solve the first term
$$\frac{\partial E}{\partial z_s} = \frac{1}{2} \sum_{k,j}(z_j(x^{(k)}-d_j^{(k)}))^2$$
* For the second term, noting that $z_s = g(a_s)$
$$\frac{\partial z_s}{\partial a_s} = g'(a_s)$$
* For the last term, noting that $a_s = \sum_i w_{is} x_i^{(k)}$ ($w_{is}$ is the weight of the connection between the input neuron $i$ and the output neuron $s$)
	* In the derivative I am only interested in input $r$, so
$$\frac{\partial a_s}{\partial w_{rs}} = x_r^{(k)}$$
* So putting everything toghether
$$\frac{\partial E}{\partial w_{rs}} = \sum_{k}(z_s(x^{(k)}-d_s^{(k)}))^2 * g'(a_s) * x_r^{(k)}$$
* The term $\sum_{k}(z_s(x^{(k)}-d_s^{(k)}))^2 * g'(a_s)$ is called $\delta_s^{(k)}$ (deviation) and depends only on the output neuron $s$, not on the input $r$
* I can therefore write everything as
$$\frac{\partial E}{\partial w_{rs}} = \sum_{k} \delta_s^{(k)} * x_r^{(k)}$$
* If the activation function is not linear, its derivative $g'(a)$ will be really variable across its domain
* The training for a single parameter converges when $$\frac{\partial E}{\partial w_{rs}} \approx 0$$
* The number of layers in a neural network can be measured according to 2 different definitions
	* The number of weight layers
		* In this framework a perceptron has 1 layer
	* The number of neuron layers
		* In this framework a perceptron has 2 layers
* The computational power of a perceptron is limited to linear relationships (or linear decision boundaries in the case of classification probelems)
	* The activation can be expresses as $\sum_i w_i x_i - \theta$, which is the equation of an i-dimensional manifold
	* Using feature crosses, I can indirectly implement non linear boundaries but those are not learnt by the perceptron, I am just translating the space to a linearly separable one
* This limitation of the perceptron is a well-known computational problem, the XOR problem
	* XOR returns 0 when the inputs are both 0 or both 1, and 1 otherwise
	* It is not possible to implement a XOR function with a perceptron, since this function is non linear
	* When it was proven that the XOR problem could not be solved by a perceptron, neural networks disappeared from the AI research for 15 years
* In order to learn non-linear relationships, I can use a feed-forward network with hidden layers
	* The number of hidden layers and the number of neurons in the hidden layers are hyperparameters
	* This is still a feed-forward network, so there is no back-communication and communication across same-layer neurons
* With a network with 1 hidden layer, I have $n$ input neurons, $m$ output neurons, and $h$ hidden neurons
* For the hidden neuron $j$ in layer 1 I have that
$$z_j^{(1)} = g(\sum_i w_{ij}^{(1)}x_i-\theta_j^{(1)})$$
* For the output layer instead the input is the output of the hidden layer ($z^{(1)}$)
$$z_j^{(2)} = g(\sum_i w_{ij}^{(2)}z_i^{(1)}-\theta_j^{(1)})$$
* With a multilayer network I can solve the XOR problem
* The hidden layer maps the input to a new space where the points are linearly separable
* In multi-layer networks using non-linear transfer function facilitates the discrimination of non-linearly-separable problems
* With deep learning is also possible to use non-derivable transfer functions like the ReLU
	* In this case the algorithm need to be changed a little bit
* With a multi-layer network I cannot use the same training strategy used for the perceptron, since I do NOT know the desired output of the hidden layer!
* For the second weight layer I can use the training formula since I know the desired output, but I do not know the input
* The input of the second layer is the output of the first layer, which I can express
* Backpropagation xxx
$$\frac{\partial E}{\partial w^{(2)}_{rs}} = \sum_k \delta_s^{(2,k)} z_r^{(1)(x^{(k)})}$$
$$\frac{\partial E}{\partial w^{(1)}_{rs}} = \sum_k \delta_s^{(2,k)} z_r^{(1)(x^{(k)})}$$
* Neural networks can be used for regression as well as for classification, without particular modifications
* Increasing the number of neurons in the hidden layer increses the risk for overfitting the data
* It can be proven that neural networks are universal approximators
	* Other universal approximators are polynomials (Stone-Weistress theorem)
* Given some general conditions, by increasing the number of hidden neurons in a layer (width) or by increasing the number of hidden layers (depth), NNs can approximate any continuous and derivable function with arbitrary precision
* The fact that NN are universal approximators exposes them to the risk of overfitting
* The number of parameters must be far lower than the number of training points in order to avoid overfitting
* A typical sign of overfitting is having weights with really high absolute value
* If possible it is good to limit the magnitude of parameters by using regularizers
* The number of parameters in a network with $n$ input neurons, $r$ hidden neurons and $k$ output neurons is $r(n+1)+(r+1)m$
* I can evaluate the performance of my network on a validation set, which I use to fix the hyperparameters
* I should always reserve a test set that is never used for the computation
* In classical NN (trained with backpropagation), increasing the width of the network is much better than increasing the depth
* How do you represent a sequence for a NN?
