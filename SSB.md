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
* A function with 2 to inputs and 1 output can be represented with level curves
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
* The gradient evaluated at a point $w_0$ is the vector of all the first order partial derivatives evaluated at that point
$$ \nabla f(x)|_{w_0}= (\frac{\partial f}{\partial x_1}|_{w_0},\frac{\partial f}{\partial x_2}|_{w_0},...,\frac{\partial f}{\partial x_n}|_{w_0})$$

## Gradient Descent
* A perceptron performs a mapping $\mathbb{R}^n \to \mathbb{R}^m$
	* $n$ is the number of inputs and $m$ the number of outputs
* The error function is a function
$$ E_{\vec{w},\theta} : \mathbb{R}^{(n+1)m} \to \mathbb{R}$$
* Training means finding the set of parameters $w$ (which includes $\theta$) that minimizes the error function
* The analytical solution of the maxima and minima of the error function is usually not computationally feasible
	* I am in a extremum (or a saddle/flexus) when all the partial derivatives of the error function are 0
	* In order to define a gradient the error function must be derivable
	* Since the error function includes the transfer function, also this must be derivable
	* This approach would be really good since it does not need any inizialization and outputs a set of all the extrema and saddle points/flexuses
	* I could then just subsitute for all of these points and find the global extrema
* An analytical procedure for finding a global extremum of a function is still an open problem
* Iterative algorithms are generally adopted,but they do not guarantee to find a global minimum
* If the desired output $d$ is binary we have a classification problem, if it is a real number a regression problem
* Gradient descent finds a LOCAL minimum of a function by always going against the gradient
* In order to compute the gradient of the error function, I need to compute the first derivative of the transfer function
	* This implies that the transfer function be derivable!
* If the activation function is not linear, its derivative $g'(a)$ will be really variable across its domain
* The derivative $g'(a)$ of the sigmoid transfer function $g(a)$ is
$$g(a)=\frac{1}{1+e^{-a}}$$
$$g'(a)=g(a)(1-g(a))$$
* Given the error function $E$ and some initial parameters $\vec{w}$, I want to evaluate the partial derivative of the error function with respect to a single parameter $w_{ij}$
$$ E(\vec{w}) = \frac{1}{2}\sum_{k,j} (z_j(x^{(k)},w)-d_j^{(k)})^2 $$
$$ \frac{\partial E}{\partial w_{ij}} = \sum_k \frac{\partial E}{\partial z_j}\frac{\partial z_j(a_j)}{\partial a_j}\frac{\partial a_j(w_{ij},x^{(k)})}{\partial w_{ij}}$$
	* This is just the chain rule on $E, z_j, a_j$
* I can decompose the first term
$$ E(z_j^{(k)},d_j^{(k)}) = \frac{1}{2}\sum_k (z_j^{(k)} - d_j^{(k)})^2$$
$$\frac{\partial E}{\partial z_j} = \sum_k z_j^{(k)}-d_j^{(k)}$$
* For the second term
$$z_j(a_j) = \frac{1}{1+e^{-a_j}} $$
$$\frac{\partial z_j(a_j)}{\partial a_j} = z_j(a_j)(1-z_j(a_j))$$
* For the last term
$$a_j(w_{ij},x^{(k)})=\sum_i x_i^{(k)}w_{ij}$$
$$\frac{\partial a_j(w_{ij},x^{(k)})}{\partial w_{ij}} = x_i^{(k)}$$
* So putting everything back toghether
$$\frac{\partial E}{\partial w_{ij}} = \sum_k (z_j^{(k)}-d_j^{(k)}) z_j(a_j)(1-z_j(a_j)) x_i^{(k)}$$
* I note that only the last term depends on the input neuron $i$, so I call all the rest (which does not depend on it) as deviation $\delta_j^{(k)}$
$$ \delta_j^{(k)}=(z_j^{(k)}-d_j^{(k)}) z_j(a_j)(1-z_j(a_j))$$
$$\frac{\partial E}{\partial w_{ij}} = \sum_k \delta_j^{(k)} x_i^{(k)}$$
* The partial derivative $\frac{\partial E}{\partial w_{ij}}$ can be used to update the weight $w_{ij}$
$$ w_{ij} = \underline{w}_{ij} - \eta \frac{\partial E}{\partial w_{ij}}|_{\underline{w}_{ij}}$$
	* $\eta$ is the learning rate, a hyperparameter
* Now that I know the partial derivative with respect to one of the weights $w_{ij}$, I can calculate it for all of the weights, obtaining the gradient $\nabla E$
* I can use gradient descent for updating all the parameters simultaneously
	* I update the parameters in the direction that would lower the error function, given the set of partial derivatives (the gradient!)
	* I can define the set of parameters $w_1$ as a function of the old set of parameters $w_0$
$$ w_1 = w_0 - \eta \nabla E|w_0$$
	* I repeat the process iteratively until $E$ is below a certain acceptable threshold
* The general gradient descent formula is thus
$$ w_{t+1} = w_t - \eta \nabla E|w_t$$
* A gradient descent converges when $\nabla E = \vec{0}$
* An high learning rate increases convergence speed, but it increases the risk of missing a minimum
* Really high learning rates could fail to converge
* In order to optimize the choice of learning rate, I can use the second order partial derivatives (Hessian matrix)

## Linear Separability
* The computational power of a perceptron is limited to linear relationships (or linear decision boundaries in the case of classification probelems)
	* The activations can be expressed as $\sum_i w_i x_i$, which is the equation of an i-dimensional manifold
	* Using feature crosses, I can indirectly implement non linear boundaries but those are not learnt by the perceptron, I am just translating the space to a linearly separable one
* This limitation of the perceptron is a well-known computational problem, the XOR problem
* XOR returns 0 when the inputs are both 0 or both 1, and 1 if they are different
* It is not possible to implement a XOR function with a perceptron, since this function is non linear
	* When it was proven that the XOR problem could not be solved by a perceptron, neural networks disappeared from the AI research for 15 years (1960 to 1980)

## Multi-layer Feed-Forward NNs
* In order to learn non-linear relationships, I can use a feed-forward network with hidden layers
	* The number of hidden layers and the number of neurons in the hidden layers are hyperparameters of the network
	* This is still a feed-forward network, so there is no back-communication and communication across same-layer neurons
* The number of layers in a neural network can be measured according to 2 different definitions
	* The number of weight layers
		* In this framework a perceptron has 1 layer
	* The number of neuron layers
		* In this framework a perceptron has 2 layers
	* I will use the number of weight layers as a definiton
* In a network with 1 hidden layer, I have $n$ input neurons, $m$ output neurons, and $h$ hidden neurons
* I put the superscript $^{(1)}$ to things belonging to the first level, and $^{(2)}$ for the second level
* The output of the first layer can be easily described
$$z_j^{(1)} = g(\sum_i w_{ij}^{(1)}x_i)$$
* The output of the second layer can be described in terms of the output of the hidden layer
$$z_j^{(2)} = g(\sum_i w_{ij}^{(2)}z_i^{(1)})$$
* With a 2-layer network I can solve the XOR problem
	* The hidden layer has 2 neurons
	* 1 of the hidden neurons (neuron A) performs and AND operation: it is active if both inputs are 1
	* The other hidden neuron (neuron B) performs and OR operation: it is active if either of the inputs is active
	* The output neuron performs B AND (NOT A): it is active if B is active but A is not
* The hidden layer maps the input to a new space where the points are linearly separable
* In multi-layer networks using non-linear transfer function facilitates the discrimination of non-linearly-separable problems
* With deep learning is also possible to use non-derivable transfer functions like the ReLU
	* In this case the algorithm need to be changed a little bit
* With a multi-layer network I cannot use the same training strategy used for the perceptron, since I do NOT know the desired output of the hidden layer!
* For the output layer I could use the training formula since I know the desired output, but I do not know its input
* The input of the second layer is the output of the first layer, which I can express as a function of the real input

## Backpropagation
* The backpropagation algorith was invented in a 1974 PhD thesis (Werbos) and extended in a 1986 paper (Rumelhart, Hinton, Williams)
* This algorithm is the most used approach for obtaining the gradient of the error function in multi-layer perceptrons
* It is called backpropagation since the cost propagates back to the network layers in order to compute the gradient
* For the second layer, I can just use the classical perceptron formula by substituting the input $x_i$ with the output of the previos layer $z_i$
$$ \frac{\partial E}{\partial w^{(2)}_{ij}} = \sum_k \delta^{(2,k)}_j z^{(1,k)}_i$$
$$\frac{\partial E}{\partial w_{ij}} = \sum_k (z_j^{(2)}(x^{(k)},w_{ij})-d_j^{(k)}) g'(a^{(2,k)}_j) z_i^{(1,k)}$$
	* I know all the terms
* For the hidden layer the situation is less clear, since I do not know what the desired output is
$$ \frac{\partial E}{\partial w^{(1)}_{ij}} = \sum_k \delta^{(1,k)}_j x^{(k)}_i$$
	* I need to derive an expression for $\delta^{(1,k)}_j$, the sensitivity of the error to a variation in the activation of a neuron in the hidden layer
* I note that the derivative of the error function with respect to a single weight of the first layer $w^{(1)}_{ij}$ can be decomposed with the chain rule as
$$ \frac{\partial E}{\partial w^{(1)}_{ij}} = \sum_k \frac{\partial E}{\partial a_j^{(1,k)}} \frac{\partial a_j^{(1,k)}}{\partial w_{ij}^{(1)}}$$
	* The sum is across the training samples
	* The first term is the derivative of the error function with respect to the activation of the neuron $j$ of the first layer (the one receiving the connection $w_{ij}$), and so it is the deviation of the neuron of the hidden layer $\delta^{(1,k)}_j$
	* The second term is the derivative of the activation of the neuron $j$ of the first layer with respect to the weight $w^{(1)}_{ij}$ of the first layer
* I note that the deviation can be further decomposed in terms of the activation of the output layer
$$\frac{\partial E}{\partial a_j^{(1,k)}} = \sum_m \frac{\partial E}{\partial a_m^{(2,k)}}\frac{\partial a_m^{(2,k)}}{\partial a_j^{(1,k)}}$$
	* The sum is across the neurons of the output layer
	* The first term is the derivative of the error function with respect to the activation of neuron $m$ of the second layer (I sum over all of them)
	* The second term is the derivative of the activation of neuron $m$ of the second layer with respect to the activation of neuron $j$ of the first layer
* The activation $a_m^{(2,k)}$ of a neuron $m$ of the second layer can be expressed in terms of the activations $a_j^{(1,k)}$ of all the neurons $j$ of the first layer
$$a_m^{(2,k)}=\sum_j z_j^{(1,k)}w_{jm}^{(2)}=\sum_j g(a_j^{(1,k)})w_{jm}^{(2)}$$
	* $g(x)$ is the transfer function
* The derivative of the activation of neuron $m$ of the second layer with respect to the activation of neuron $j$ of the first layer can thus be expressed as
$$\frac{\partial a_m^{(2,k)}}{\partial a_j^{(1,k)}}=g'(a_j^{(1,k)})w_{jm}^{(2)}$$
	* The sum disappears since all the terms besides the one relative to neuron $j$ are constants and thus have a derivative of 0
* Thus I can define $\delta^{(1,k)}_j$ as
$$ \delta^{(1,k)}_j = \frac{\partial E}{\partial a_j^{(1,k)}} = \sum_m \delta^{(2,k)}_m g'(a_j^{(1,k)}) w_{jm}^{(2)}$$
	* This is because
$$\delta^{(2,k)}_m = \frac{\partial E}{\partial a_m^{(2,k)}}$$
* In the backpropagation algorithm I proceed as follows for a single output neuron $m$
	* I compute the output $z^{(2,k)}_m$ for each example $k$ (feed-forward step)
	* From the output, I compute the deviation of the second layer $\delta^{(2,k)}_m$
	* I compute the deviation of the hidden layer $\delta^{(1,k)}_j$ from the deviation of the output layer, the activation of the first layer and the weights connecting the 2 layers
	* I compute then the gradient $\nabla E$ with respect to all the weights $w$
	* I perform gradient descent on $\nabla E$
* In the update I can also add an inertial hyperparameter $\alpha$ (called momentum) to speed up the training
$$w_{ij}^{t+1}=w_{ij}^t-\eta\frac{\partial E}{\partial w_{ij}}+ \alpha \Delta w_{ij}^t$$
	* This makes update bigger when previous updates where bigger, and smaller when they where smaller

## Final Thoughts
* Neural networks can be used for regression as well as for classification without particular modifications
	* I just replace the desired class $d$ with a desired continuous output $y$
* In a regression problem the desired outputs are real numbers, in a classification problem they are either 0 or 1
* Increasing the number of neurons in the hidden layer increses the risk for overfitting the data
* It can be proven that neural networks are universal approximators
* Given some general conditions, by increasing the number of hidden neurons in a layer (width) or by increasing the number of hidden layers (depth), NNs can approximate any continuous and derivable function with arbitrary precision
* Other universal approximators are polynomials (Stone-Weistress theorem)
* The fact that NN are universal approximators exposes them to the risk of overfitting
* The number of parameters must be far lower than the number of training points in order to avoid overfitting
* A typical sign of overfitting is having weights with really high absolute value
* If possible it is good to limit the magnitude of parameters by using a regularizer $\lambda$
$$E=\frac{1}{2}\sum_{k,j}(z_j(x^{(k)},w)-y^{(k)}_{ij})^2+\lambda\sum (w_{ij^{(k)}})^2$$
	* The regularizer penalizes the use of weights with large absolute value
* I can evaluate the performance of my network on a validation set, which I use to fix the hyperparameters
* I should always reserve a test set that is never used for the computation
* Backpropagation is not suitable for training deep networks: we need deep learning procedures
* The number of parameters in a network with $n$ input neurons, $r$ hidden neurons and $k$ output neurons is $r(n+1)+(r+1)m$
* In classical NN (trained with backpropagation), increasing the width of the network is much better than increasing the depth
* Representing a sequence for a neural network can be done using a input neuron for each possible symbol
* Deep networks cannot be trained with backpropagation since the backpropagated effect to deep hidden layers is so small that no effective training is possible

# Support Vector Machines
* A simple perceptron with an heaviside activation function produces an output $z>0$ iff the activation is bigger than 0
$$ z_j>0 \iff \sum_i w_{ij} x_i - \theta_j > 0$$
* For each of its outputs $z_j$, a perceptron like this effectively defines an hyperplane that splits the input space with equation
$$ \vec{w_j} \vec{x} - \theta_j = 0$$
* Given 2 classes of input points for a linearòy separable problem, there can be many correct decision boundaries
* A perceptron can find one of such boundaries, but intuitively these boundaries are not all equally good
* In general, I want my decision boundary to be as far from the datapoints as possible: I want to maximise the margin between the decision boundary and the nearest datapoints
* A SVM (Support Vector Machine) finds the hyperplane that solves a linearly separable problem  and maximizes the distance among the hyperplane itself and any of the datapoints
	* This minimizes the risk for misclassification
	* The distance among the hyperplanes passing on the closest datapoints of the 2 classes is the margin
	* The decision boundary is choosen as an hyperplane parallel to the 2 margin hyperplanes and equally distant ot both of them
* A kernel is a generalization of SVMs that implements non-linear decision boundaries

## Vectors and Hyperplanes
* The dot product of 2 vectors is the product of their norm, multiplide by the angle between them
$$<\vec{a}\vec{b}>=|\vec{a}||\vec{b}|\cos \theta$$
	* The result is a scalar
	* The product of the norm of one of the vectors times the angle between them is the norm of the projection of the first vector onto the other
	* The dot product is the projection of one vector onto the other scaled by the magnitude of the second vector
	* The scalar product is 0 when the projection of one vector onto the other is 0, when they are normal to each other ($cos 90° = 0$)
	* A 0 scalar product means that 2 vectors are normal to each other
* An hyperplane passing through the origin can be represented as the set of vectors $\vec{x}$ that are normal (i.e. they have a 0 projection) to defining vector $\vec{w}$
$$<\vec{x}\vec{w}> = 0$$
* Any hyperplane can be represented as the set of vectors $\vec{x}$ that have a certain constant projection (positive or negative) on a defining vector $\vec{w}$
$$<\vec{x}\vec{w}>+b = 0$$
	* The hyperplane itself is always normal to $\vec{w}$, but the vectors defining the points on the hyperplane are not and they have a constant non-zero projection on $\vec{w}$
	* The projection of a vector $\vec{x}$ on $\vec{w}$ is
$$|\vec{x}|\cos \theta = \frac{<\vec{x}\vec{w}>}{|\vec{w}|} = -\frac{b}{|\vec{w}|}$$
	* If we define $b$ so that $\frac{b}{|\vec{w}|}$ is the negative projection of a vector $\vec{x}$ onto $\vec{w}$, then
$$\frac{<\vec{x}\vec{w}>}{|\vec{w}|} + \frac{b}{|\vec{w}|} = 0 \iff <\vec{x}\vec{w}>+b = 0$$
	* The sign of $b$ depends on the direction of $\vec{w}$ with respect to $\vec{x}$

## Margins and Classification
* The margin can be defined as the distance among 2 parallel hyperplanes that are the closest possible to the decision boundary and that pass through a point respectively in the 2 classes
* Each of these hyperplanes is defined by the same vector $\vec{w}$ and by a different $b_i$
* I can calclulate the margin $m$ as the difference between the projections of the hyperplane onto $\vec{w}$
$$m = \frac{|b_2-b_1|}{|w|}$$
* I can choose $\vec{w}$ and $b$ so that the decision boundary and the margins are as follows
$$ dec\_bound =  <\vec{w}\vec{x}> + b = 0 $$
$$ marg_1 = <\vec{w}\vec{x}> +b = -1 $$
$$ marg_2 = <\vec{w}\vec{x}> +b = +1 $$
* In this case, the margin $m$ is $\frac{2}{|\vec{w}|}$
$$ marg_1 = <\vec{w}\vec{x}> +b_1 = 0,\ marg_1 = <\vec{w}\vec{x}> +b = -1 \implies b_1 = b+1$$
$$ marg_2 = <\vec{w}\vec{x}> +b_2 = 0,\ marg_2 = <\vec{w}\vec{x}> +b = +1 \implies b_2 = b-1$$
$$m = \frac{|b_1-b_2|}{|w|} \implies m = \frac{(b+1)-(b-1)}{|\vec{w}|}$$
$$m = \frac{2}{|\vec{w}|}$$
* Since I defined then the margin $m = \frac{2}{|\vec{w}|}$, the SVM problem of maximizing the margin becomes the problem of minimizing $|\vec{w}|$
	* I need to exclude the trivial case $|\vec{w}|=0$, that does not define any hyperplane
	* It is easier to minimize actually the square of the norm of $\vec{w}$, $|\vec{w}|^2$, since this is a derivable function while the norm itself is not
	* Actually, to simplify the derivatives we minimize the quantity $\frac{1}{2}|\vec{w}|^2$
* To understand if a point is on one side or the other of an hyperplane, I can compare its projection on $\vec{w}$ with the projection of the hyperplane on $\vec{w}$
	* If the projection is greater, the point is more on the direction where $\vec{w}$ points than the hyperplane
* The goal of SVM is to find a $\vec{w}$ such that $|\vec{w}|$ is minimal but not 0
* Let $\{x1, x_2, ..., x_i\}$ be our data point with $\{y_1, y_2, ..., y_i\}$ their class label such that $y_i \in \{-1,1\}$
	* A point $x_i$ with $y_i = -1$ belongs to the negative class, while if $y_i = 1$ it belongs to the positive class
* Since I defined the margin as having scaled projections of 1 and -1, I want to define $\vec{w}$ such that all the points to fall on the correct side of the margins
$$y_i = 1 \implies <\vec{x_i}\vec{w}>+b > 1$$
$$y_i = -1 \implies <\vec{x_i}\vec{w}>+b > -1$$
* I can summarise this condition as
$$ y_i(<\vec{x_i}\vec{w}>+b) \geq 1 \ \forall \ i$$
* I can then define the goal of a SVM as minimizing $\frac{1}{2}|\vec{w}|^2$ under the constraints $y_i(<\vec{x_i}\vec{w}>+b) \geq 1 \ \forall \ i$
	* The number of constraint is equal to the number of training data
* This is a constrained optimization problem, that can be tackled using Lagrange multipliers

## Lagrange Theory
* I want to maximize the function $z = f(x,y)$ subject to the constraint $g(x,y) = c$
* The constraint defines a n-1 dimensional curve $y=h(x)$ in the x,y plane such that $g(x,y)=g(x,h(x))=c$
* The naive solution would be to solve the constraint by defining $h(x)$, and then finding the maximum in $x$ of $g(x,h(x))$
	* This analytical solution can be very difficult
* A level curve on the $z=f(x,y)$ surface can be defined as a set of points such that $f(x,y)=d$
* In order to maximise the function $f(x,y)$ under the constraint $g(x,y)=c$, I can walk along the constraint until I find a point of tangency with a level curve
	* If the constraint is tangent to a level curve, that point is either a maximum or a minimum (or a flexus) of $f(x,y)$ under the constraint
* The constraint is tangent to a level curve if the local normal to the constraint and to the level curve are parallel
* The direction that is normal to the level curve of a function is the gradient of the function
* For the constraint $g(x,y)=c$, the gradient $\nabla g$ is
$$ \nabla g = (\frac{\partial g}{\partial x}, \frac{\partial g}{\partial y})$$
* I move from $g(x,y)=c$ to another point on the constraint $g(x+\epsilon_x,y+\epsilon_y)=c$
* If $\epsilon_x,\epsilon_y$ are small
$$g(x+\epsilon_x,y+\epsilon_y) \approx g(x,y)+\epsilon_x \frac{\partial g}{\partial x}|_{(x,y)}+\epsilon_y \frac{\partial g}{\partial y}|_{(x,y)}$$
$$g(x+\epsilon_x,y+\epsilon_y) \approx g(x,y)+\vec{\epsilon} \ \nabla g|_{(x,y)}$$
* Since both points are on the constraint
$$c \approx c+\vec{\epsilon} \ \nabla g|_{(x,y)}$$
* As a consequence, the gradient must be perpendicular to the local movement along the constraint
$$\vec{\epsilon} \ \nabla g|_{(x,y)} = 0$$
* The extrema of $f(x,y)$ that respect the constraint must have a gradient which is parallel to the gradient of the constraint itself and where the constraint is respected
$$ \nabla f = \lambda \nabla g$$
$$ g(x,y)=c$$
	* 2 vectors are parallel if they are equal, allowing for a scalar factor
	* The scalar factor $\lambda$ is called Lagrange multiplier
* If $\lambda < 0$ the 2 gradients point in opposite directions, if $\lambda > 0$ they point in the same direction
	* If $\lambda=0$ it means that $f(x,y)$ is flat (its gradient is the 0 vector)
* I introduce the Lagrangian function to incorporate all of these conditions
$$\mathcal{L}(x,y,\lambda) = f(x,y) - \lambda*(g(x,y)-c)$$
* If instead of a constraint $g(x)=c$ I equivalently define it as $g(x)=0$, and instead of $x,y$ I define an input vector $\vec{x}$
$$\mathcal{L}(\vec{x},\lambda) = f(\vec{x}) - \lambda*(g(\vec{x})$$
* I can find the tangency points by solving for the gradient of the Lagrangian
$$ \nabla \mathcal{L}_{x_i,\lambda} = 0$$
* The gradient of the Lagrangian provides the corrent solution since it can be decomposed as
$$\nabla \mathcal{L}_{x_i,\lambda} = 0 \implies \begin{cases} \frac{d\mathcal{L}}{dx_i} = 0 \\  \frac{d\mathcal{L}}{d\lambda} = 0 \end{cases}$$
* Which can be expanded further
$$\frac{d\mathcal{L}}{dx_i} = 0 \implies \nabla f_x - \lambda \nabla g_x = 0$$
$$\frac{d\mathcal{L}}{d\lambda} = 0 \implies g(\vec{x}) = 0$$
* Which were the original constraints

## KKT (Karush-Kuhn-Tucker) Conditions
* I can define the goal of a SVM as minimizing $\frac{1}{2}|\vec{w}|^2$ under the constraint $y_i(<\vec{x_i}\vec{w}>+b) \geq 1 \ \forall \ i$
* This problem is similar to the Lagrange problem, but it requires a constraint $g(\vec{x}) \geq 0$ instead of $g(\vec{x})=0$
* This kind of constraint instead of defining a curve in the x,y plane, divides the plane in 2 regions, one in which $g(x,y)< 0$ and one in which $g(x,y)\geq 0$
* The boundary of the 2 regions is the classic Lagrange constraint $g(x,y)=0$
* My problem is to maximize-minimize $f(\vec{x})$ under the constraint $g(\vec{x})\lessgtr 0$
* Let's suppose that I have a point $x_0$ of maximum or minimum of the function along the constraint
$$x_0 : \ \nabla f|_{x=x_0} = \lambda \nabla g|_{x=x_0}$$ 
* Let my constraint be $g(\vec{x})\leq 0$ and my goal to minimize $f(\vec{x})$
	* If $\lambda >0$ the gradients of the constraint and of the function are parallel at $x_0$
		* I want to minimize the function, and the function decreases by going away from the constraint in the allowed region of space
		* The minimum of the function CANNOT be on the contraint
		* In this case the presence of the constraint does not alter the solution, which is said to be internal
	* If $\lambda < 0$ the gradients of the constraint and of the function are antiparallel at $x_0$
		* I want to minimize the function, and the function increases by going away from $g\vec{x})=0$ in the allowed region of space
		* The minimum of the function MUST be on the contraint
* If my goal is a maximization and not a minimization, or if the constraint is in the form $g(\vec{x}) \geq 0$ the situation is of course reversed
* A function $f(\vec{x})$ is under a set of constraints $g_i(\vec{x}) \leq 0$ or $g_i(\vec{x}) \geq 0$ and I want to either minimize or maximise $f(\vec{x})$ under the constraints
* In the KKT conditions literature the Lagrangian is defined using $\alpha = -\lambda$
$$\mathcal{L}(\vec{x},\alpha) = f(\vec{x})+\alpha g(\vec{x})$$
$$\nabla f(\vec{x}) = -\alpha \nabla g(\vec{x})$$
	* Note that in the KKT theory the second term is added and not subtracted
	* This does not change anything in practice, but $\alpha$ as an opposite sign compared to $\lambda$ when determining the direction of the gradient
* The KKT conditions are statements about the sign of $\alpha$
	* If $g(\vec{x}) \leq 0$ and I want to minimize $f(\vec{x})$, then I impose that $\alpha \geq 0$
	* If $g(\vec{x}) \leq 0$ and I want to maximize $f(\vec{x})$, then I impose that $\alpha \leq 0$
	* If $g(\vec{x}) \geq 0$ and I want to minimize $f(\vec{x})$, then I impose that $\alpha \leq 0$
	* If $g(\vec{x}) \geq 0$ and I want to maximize $f(\vec{x})$, then I impose that $\alpha \geq 0$
* The reason for these restrictions on $\alpha$ is that, according to the kind of constraint ($\leq 0$ or $\geq 0$) and the desired optimization problem (minimization or maximization), an $\alpha$ that does not respect those conditions denotes a constraint that is not acting, and thus must be removed in the minimization of the Lagrangian
* From these statements about $\alpha$, I can derive the complementarity condition
$$ \alpha_i g_i(\vec{x}) = 0 \ \forall \ i$$
	* If $\alpha = 0$, then the constraint is not acting and the condition is respected
	* If $\alpha \not= 0$, then the constraint is acting, and thus the solution must be on the constraint itself: $g_i(\vec{x}) = 0$
* In SVM optimization, the function $f(\vec{x})$ is a function of the norm of $\vec{w}$, and the constraints $g_i(\vec{x})$ are position of the points with repsect to the margins
$$f(\vec{x}) = \frac{1}{2}|\vec{w}|^2$$
$$g_i(\vec{x}_i) = y_i(<\vec{x}_i\vec{w}>+b) \geq 1$$
* I can rewrite the constraint as
$$g_i(\vec{x}_i) = y_i(<\vec{x}_i\vec{w}>+b)-1 \geq 0$$
* If I want the constraint to be in the form $g(\vec{x}) \leq 0$
$$g_i(\vec{x}_i) = 1-y_i(<\vec{x}_i\vec{w}>+b) \leq 0$$
* In this framework ($g(\vec{x}) \leq 0$) and with a minimization goal on $f(\vec{x})$ (I want to minimize the norm of $\vec{w}$!), from the KKT conditions I have that
$$\alpha_i \leq 0$$
$$\alpha_i g_i(\vec{x}) = 0$$
	* 





* I can define the solution $x$ as a function of the multipliers $\alpha_i$
* If I substitute these definition of $x$ in place of $x$ in the KKT Lagrangian, I obtain the dual Lagrangian
* A constraint $g(\vec{x})=0$ with $\vec{x} \in \mathbb{R}^n$ defines an $n-1$ dimensional manifold
	* The constraint represents all the points of $g(\vec{x})$ which are cut by an hyperplane centered in $g=0$
* This constraint divides the space in 2 regions, one where $g(\vec{x})>0$ and one where $g(\vec{x})\leq 0$
* I want to minimize a function $f(\vec{x})$ by in the portion of space where $g(\vec{x})\leq 0$
* If the gradients of the 2 functions at a point point in the same direction, the point cannot be an allowed minimum
$$ \vec{\nabla f}|_{\vec{x}=0} = \lambda \vec{\nabla g}|_{\vec{x}=0}$$
$$\lambda > 0$$
	* I can decrease the function by remaining in the allowed region
	* The solution is internal and not on the constraint
* If the gradients of the 2 functions at a point point in the opposite directions, the point can be a minimum
$$ \vec{\nabla f}|_{\vec{x}=0} = \lambda \vec{\nabla g}|_{\vec{x}=0}$$
$$\lambda \leq 0$$
	* In order to decrease the function I should go in the disallowed region
	* In this case the solution is on the constraint
* The convention of the KKT theory is to use a multiplier with opposite sign to the one used in the Lagrange theory
* xxx check after whatching recordings

## Soft Margin SVM
* When problems are not linearly separable, I can implement a soft margin
* I add a slack variable $\zeta \geq 0$ that represent the error in the classification for each point
	* The slack variable is greater than 0 only for points that are on the wrong side of the margin, otherwise it is 0
* The new conditions for the SVM margins become
$$ marg_1 = <\vec{w}\vec{x}> +b = -1 + \zeta$$
$$ marg_2 = <\vec{w}\vec{x}> +b = +1 - \zeta$$
* The quantity to be minimized include now also the sum of the slack variables
$$\frac{1}{2}|\vec{w}|^2 + C \sum_i \zeta_i$$
	* The hyperparameter C determines the relative weight of the error and of the margin width on the determination of the margin hyperplanes
	* A large C makes the soft margin behave more like an hard margin
* Soft margins tend to be more robust to noise in the data, and are practically almost always used

## Kernel Methods
* I cannot use a linear SVM to solve non linearly separable problems
* I can map the original input space to a linearly separable feature space, which I can solve with SVMs
	* The input vector $\vec{x} \in \mathbb{R}$ is transformed to the feature vector $\vec{\phi}(\vec{x}) \in \mathbb{R}$
* In order to apply the SVM to the feature space, I define the dual Lagrangian on the feature space
* A kernel $K$ is a function of 2 input points $\vec{x}$,$\vec{z}$ that replaces the scalar product in the SVM objective function, to implicitly implement a translation of the input to the feature space
$$ K(\vec{x},\vec{z})=<\vec{\phi}(\vec{x}),\vec{\phi}(\vec{z})>$$
* I do not want to craft a feature space that is specific to the problem, but I can apply some general concepts
* Increasing the dimensionality of the input space increases the number of hyperplanes and thus the likelyhood of linear separability
* I can define a kernel as a simple function of the components of the vectors
$$ K(\vec{x},\vec{z})=<\vec{\phi}(\vec{x}),\vec{\phi}(\vec{z})>$$
$$\vec{\phi}(\vec{x}) = (1,\sqrt{2}x_1,\sqrt{2}x_2,\sqrt{2}x_1x_2,x_1^2,x_2^2)$$
$$\vec{\phi}(\vec{z}) = (1,\sqrt{2}z_1,\sqrt{2}z_2,\sqrt{2}z_1z_2,z_1^2,z_2^2)$$
* I can create a very high-dimensional feature space withouth actually storing these high dimensional points
* The only thing that I need from the feature space is the definition of the scalar product in that space
	* I only need to do a scalar product of the vectors in the objective function
	* I can just derive the scalar product from a kernel once, and use it always without actually dealing with the high-dimensional space
* Many different functions can work as kernels
	* They just need to be symmetric and to repsect a set of conditions
* A kernel is actually just a measure of similarity between $\vec{x}$ and $\vec{z}$
	* I am not restricted to use a vector as input
	* In bioinformatics it is not very useful to use non-standard kernels
* Kernels are not only used for SVM, they can be used wherever only scalar products need to be defined
	* They are also used in PCA and other classification techniques
* A stationary kernel is defined in terms of a difference between inputs
$$K(x_i,x_j)=k(x_i-x_j)$$
	* They are called stationary since they are invariant to translations of the input space
* A radial basis function kernel (or homogeneous kernel) measure the euclidean distance among points
$$K(x_i,x_j)=k(||x_i-x_j||)$$
* The homogeneous polynomial kernel is defined as
$$ K(x^i,x^j)=(<x_i x_j>)^d$$
	* This kernel includes all the possible expansions of the degree $d$ of the vector components
	* The number of dimensions for an homogeneous polynomial kernel of grade $d$ with an input space $\mathbb{R}^n$ is $~ n^d$ for $n >> d$
* The classic SVM without kernel can be seen as an homogeneous polynomial kernel of degree $1$
$$ K(x^i,x^j)=<x_i x_j>$$
* The polynomial kernel is defiend as
$$ K(x^i,x^j)=(1+<x_i x_j>)^d$$
	* This kernel is more widely adopted since it includes all the possible combinations of degree up to $d$ (it has many more dimensions!)
	* Also here the number of dimension grows like $n^d$
* The degree of the polynomial kernel influences the likelyhood of overfitting the data
* An high degree polynomial tends to increase the number of support vectors
	* This is because the curve tends to fit the data as well as possible
	* A way to limit overfitting is to assure that the number of support vectors is much smaller than the total number of points
* The RBF kernel is defined as
$$K(x_i,x_j) = e^{\frac{(x_i-x_j)^2}{2\sigma^2}} = e^{-\beta (x_i-x_j)^2}$$
* It can be viewed as a generalization of a polynomial kernel with infinite degree
	* This is because an exponential can be approximated by an infintite polynomial sum
* Small polynomial degrees have a large weight, while high degrees have less weight
* The value of the kernel is big when the difference between $x_i,x_j$ is big, and tends rapidly to 0 otherwise
* The hyperparameter beta (or sigma) determines the width of the curve
	* They determine the scale of the diffenrence among points that is considered significant for the kernel
	* A small sigma creates a more complex hyperplane
	* Whith extremely small sigmas, all the points become support vectors
	* A large sigma tends to a linear discrimination
* The Spectral kernel uses sequence similarity as a measure
	* In general, non-vector kernels are not so effective, but they are an intriguing
