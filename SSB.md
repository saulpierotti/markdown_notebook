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
* A SVM finds the hyperplane that solves a linearly separable problem  and maximizes the distance among the hyperplane itself and any of the datapoints
	* This minimizes the risk for misclassification
	* The distance among the hyperplane and any of the datapoints is called margin
* An hyperplane can be represented as the set of points $\vec{x}$ that are perpendicolar to a given vector $\vec{w}$ and have a certain constant projection $b$ on $\vec{w}$
$$<\vec{w}\vec{x}> +b = 0$$
	* The sign of the projection $b$ depends on the direction of $\vec{w}$
* The margin can be defined as 2 parallel hyperplanes that are the closest possible to the decision boundary that pass through a point respectively in the 2 classes
* Each of these hyperplanes is defined by the same vector $\vec{w}$ and by a different projection $b_i$
* I can calclulate the margin as
$$m = \frac{|b_2-b_1|}{|w|}$$
* If I choose $\vec{w}$ and $b$ so that the decision boundary and the margins are as follows, the margin is $m = \frac{2}{|\vec{w}|}$
$$ dec\_bound =  <\vec{w}\vec{x}> +b = 0 $$
$$ marg_1 = <\vec{w}\vec{x}> +b = -1 $$
$$ marg_2 = <\vec{w}\vec{x}> +b = +1 $$
$$m = \frac{2}{|\vec{w}|}$$
* Since I defined then the margin $m = \frac{2}{|\vec{w}|}$, the problem of maximizing the margin becomes the problem of minimizing $|\vec{w}|$
	* I need to exclude the trivial case $|\vec{w}|=0$, that does not define any hyperplane
* To understand if a point is on one side or the other of an hyperplane, I can compare its projection on $\vec{w}$ with the projection on it of the hyperplane

