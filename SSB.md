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
$$\alpha_i \geq 0$$
$$\alpha_i g_i(\vec{x}) = 0$$
	* If $\alpha_i > 0$ then $g_i(\vec{x})=0$ 
		* The constraint is acting, and so the solution is on the constraint
	* If $\alpha_i = 0$ then $g_i(\vec{x})$ can be different from 0
		* The constraint is not acting, and so $\alpha_i=0$ cancel it from the calculation

## Dual Lagrangian
* Taking into account the KKT conditions, I can write the standard Lagrangian for that serves as objective function for the SVM optimization
$$\mathcal{L}(\vec{x},\alpha_i) = f(\vec{x}) + \sum_i \alpha_i * (g_i(\vec{x})$$
* In the case of SVM optimization, I have that
$$f(\vec{w})=\frac{1}{2}|\vec{w}|^2=\frac{1}{2}<\vec{w},\vec{w}>$$
$$g_i(\vec{w},b)=1-y_j(<\vec{w},\vec{x}>+b) \leq 0$$
$$\alpha_i g_i(\vec{w},b)=0$$
$$\alpha_i \geq 0$$
* So I can rewrite the Lagrangian as
$$\mathcal{L}(\vec{w},b,\alpha^i) = \frac{1}{2}<\vec{w},\vec{w}> + \sum_i \alpha^i * [1-y^i(<\vec{w},\vec{x}^i>+b)]$$
* I can obtain the Dual Lagrangian by equating the partial derivatives of the Lagrangian with respect to $\vec{w}$ and to b to 0, and substitute these expression in the original Lagrangian
	* In this way only $\alpha_i$ remains as a variable in the optimization
	* This corresponds to restricting the solution space to those regions where the partial derivatives of $\vec{w}$ and $b$ are 0
	* The minimization of the Lagrangian corresponds to the maximization of the Dual Lagrangian
	* The Dual Lagrangian is a convex function, so I am guaranteed to find a global maximum
* I equate the partial derivative with respect to $\vec{w}$ to 0 to obtain an expression for $\vec{w}$ itself
$$\frac{\partial \mathcal{L}}{\partial \vec{w}}=0$$
	* The derivative with respect to a vector is just the derivative with respect to all of its components
$$\frac{\partial \mathcal{L}}{\partial w_r}=0 \ \forall \ r$$
	* By remembering that $|\vec{w}|^2 = <\vec{w},\vec{w}> \sum_r w_r^2$ and $<\vec{w},\vec{x}>=\sum_r w_r x_r$
$$w_r - \sum_i \alpha^i y^i x^i_r =0$$
$$w_r= \sum_i \alpha^i y^i x^i_r$$
	* Recomponing the vector from the single components
$$\vec{w}=\sum_i \alpha^i y^i \vec{x}^i$$
* By equating the partial derivative of $b$ to 0
$$\frac{\partial \mathcal{L}}{\partial b}=0$$
$$\sum_i \alpha^i y_i = 0$$
	* I can recall that b just translates the decision hyperplane
	* This condition expresses the fact that the Lagrange multipliers of the points of the 2 classes must cance out, and so must be balanced
* Now I can substitute the expression for $\vec{w}$ in the original Lagrangian
$$\mathcal{L}(\vec{w},b,\alpha^i) = \frac{1}{2}<\vec{w},\vec{w}> + \sum_i \alpha^i * [1-y^i(<\vec{w},\vec{x}^i>+b)]$$
$$\mathcal{L'}(b,\alpha^i) = \frac{1}{2}<\sum_i \alpha^i y^i \vec{x}^i,\sum_j \alpha^j y^j \vec{x}^j> + \sum_i \alpha^i * [1-y^i(<\sum_j \alpha^j y^j \vec{x}^j,\vec{x}^i>+b)]$$
$$\mathcal{L'}(b,\alpha^i) = \frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i * [1-y^i(\sum_j \alpha^j y^j <\vec{x}^j,\vec{x}^i>+b)]$$
$$\mathcal{L'}(b,\alpha^i) = \frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i - \sum_i \alpha^i y^i(\sum_j \alpha^j y^j <\vec{x}^j,\vec{x}^i>+b)$$
	* Factorizing the scalar product
$$\mathcal{L'}(b,\alpha^i) = \frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i - \sum_i \alpha^i y^i \sum_j \alpha^j y^j <\vec{x}^j,\vec{x}^i> - \sum_i \alpha^i y^i b$$
$$\mathcal{L'}(b,\alpha^i) = \frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> - \sum_i \sum_j \alpha^i y^i \alpha^j y^j <\vec{x}^j,\vec{x}^i> + \sum_i \alpha^i - \sum_i \alpha^i y^i b$$
$$\mathcal{L'}(b,\alpha^i) = (\frac{1}{2}-1)\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i - \sum_i \alpha^i y^i b$$
$$\mathcal{L'}(b,\alpha^i) = -\frac{1}{2} \sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i - \sum_i \alpha^i y^i b$$
	* Since $\sum_i \alpha^i y^i = 0$, the last term disappears and the function does not depend on b anymore
$$\mathcal{L'}(\alpha^i) = -\frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i$$
* So the Dual Lagrangian that needs to be MAXIMISED for the SVM problem is
$$\mathcal{\bar{L}}(\alpha^i) = -\frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i$$
* Always under the KKT conditions
$$\alpha_i [1-y_j(<\vec{w},\vec{x}>+b)]=0 \ \forall \ i$$
$$\alpha_i \geq 0 \ \forall \ i$$
* The maximization of the Dual Lagrangian is a Quadratic Programming (QP) problem, since $\alpha_i$ appears at most as a bilinear term

## Quadratic Programming
* QP is the problem of optimizing a quadratic objective function and is one of the simplest forms of non-linar programming
* In a QP problem the objective function can contain bilinear and up to quadratic polynomial terms
* The constraints are linear and can be equalities or inequalities
* Many approaches have been proposed to solve QP problems
	* Logo, cplex, ...
* Most of them are interior-point methods
	* They start from an initial solution that can violate the constraints
	* They improve the solution by optimizing the objective function and reducing the amount of constraint violation
* For SVM, the most popular approach is the Sequential Minimization Optimization (SMO)
	* A QP problem in 2 variables is trivial to solve
	* Each SMO iteration picks a pair of variables $\alpha^i,\alpha^j$ and solves the QP with them
	* The approach is repeated until convergence
* We can treat the QP solver as a black box

## Solution of the SVM optimization
* The maximization of the Dual Lagrangian is a Quadratic Programming (QP) problem, since $\alpha_i$ appears at most as a bilinear term
	* This implies that a global maximum wrt $\alpha_i$ can always be found
* Once I find all the $alpha_i$, I can obtain $\vec{w}$
$$ w_r = \sum_i \alpha^i y^i x^i_r$$
* In the solution, many of the $\alpha_i$ will be 0
	* This means that many of the training points do not influence the solution
* The points $\vec{x}^i$ with $\alpha^i \not= 0$ are the support vectors
* Therefore, $\vec{w}$ can be expressed just in term of the $s$ support vectors $\vec{x}_t$
$$ w_r = \sum_{j=1}^s \alpha_t^j y_t^j {x_t^j}_r$$
* Note that there is no need to form $\vec{w}$ explicitly
* If I have a new datapoint $\vec{z}$ that I want to classify with a trained SVM
	* I compute the function
$$f(\vec{z}) = <\vec{w},\vec{z}>+b=\sum_{j=1}^s \alpha_t^j y_t^j (\vec{x}_t^j \vec{z})+b$$
	* If the function is positive the points is assigned to the class 1, if it is negative to -1
* The fact that the Dual Lagrangian is a QP problem means that SVM provide a globally optimal solution at a very low computational cost

## Soft Margin SVM
* When problems are not linearly separable, I can implement a soft margin
* I add a slack variable $\zeta \geq 0$ that represent the error in the classification for each point
* The slack variable is greater than 0 only for points that are on the wrong side of the margin, otherwise it is 0
* The new conditions for the SVM for each training point $\vec{x}_i$ become
$$ \begin{cases}
<\vec{w}\vec{x}_i> +b \geq 1 - \zeta_i    & y_i = 1 \\
<\vec{w}\vec{x}_i> +b \leq - 1 + \zeta_i  & y_i = -1\\
\zeta_i \geq 0 & \forall \ i
\end{cases}$$
* I want as always to minimize the norm of $\vec{w}$, but in soft margin SVM I want also to minimize the error $\zeta_i$ for each training point
* The quantity to be minimized thus includes now also the sum of the slack variables
$$\frac{1}{2}|\vec{w}|^2 + C \sum_i \zeta_i$$
	* Subject to
$$y_i (<\vec{w}\vec{x}_i> +b) \geq 1 - \zeta_i$$
$$\zeta_i \geq 0$$
	* This can be rewritten as
$$1 - \zeta_i - y_i (<\vec{w}\vec{x}_i> +b) \leq 0$$
$$-\zeta_i \leq 0$$
* The hyperparameter C determines the relative weight of the error and of the margin width on the determination of the margin hyperplanes
* A large C makes the soft margin behave more like an hard margin
* We can see an hard margin SVM as a soft margin SVM with $C=\infty$
* Soft margins tend to be more robust to noise in the data, and are practically almost always used
* I can rewrite the SVM Lagrangian to include the slack variables and the fact that they must be all greater than 0
$$\mathcal{L}(\vec{w},b,\zeta^i,\alpha^i,\mu^i) = \frac{1}{2}<\vec{w},\vec{w}> + C \sum_i \zeta^i + \sum_i \alpha^i * [1-\zeta^i-y^i(<\vec{w},\vec{x}^i>+b)]+\sum_i \mu^i(-\zeta^i)$$
	* In this case besides the $\alpha_i$ there are other Lagrange multipliers for the slack variables, $\mu_i$
	* In the last term $\zeta^i$ is negative since in this way $\mu^i$ is subject to the same KKT conditions as $\alpha^i$
	* Under the KKT conditions all the multipliers must be positive
$$\alpha^i \geq 0 \ \forall  i$$
$$\mu^i \geq 0 \ \forall  i$$
	* And the product of the multiplier and teh constraint must be 0
$$\alpha^i [1-\zeta^i-y^i(<\vec{w},\vec{x}^i>+b)]=0 \ \forall i$$
$$\mu^i(-\zeta^i) = 0 \ \forall i \implies \mu^i \zeta^i = 0 \ \forall i$$
* From this I can derive the Dual Lagrangian
* I impose that the partial derivative of the Lagrangian with respect to $\vec{w}$ and $b$ be 0
$$\frac{\partial \mathcal{L}}{\partial \vec{w}}=0$$
$$\frac{\partial \mathcal{L}}{\partial b}=0$$
	* $\vec{w}$ and $b$ appears exactly on the same components as for the hard margin SVM
	* I just recover the solutions previously obtained
$$\vec{w} = \sum_i \alpha^i y^i \vec{x}^i$$
$$\sum_i \alpha^i y^i = 0$$
* I impose that the partial derivative of the Lagrangian with respect to $\zeta^i$ be 0
$$\frac{\partial \mathcal{L}}{\partial \zeta^i}=0$$
$$C - \alpha^i - \mu^i = 0$$
$$\alpha^i = C - \mu^i$$
	* Since for the KKT conditions both multipliers are positive I observe that
$$ 0 \leq \alpha_i \leq C$$
	* This last equation is the only real difference for soft margin SVM with respect to hard margin SVM
* Thus the Dual Lagrangian, that depends only on $\alpha^i$, is identical to the one for the hard margin SVM
$$\mathcal{\bar{L}}(\alpha^i) = -\frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i$$
* But the constraints are different, since I have now an hyperparameter that defines an upper bound on $\alpha^i$
$$\alpha_i [1-y_j(<\vec{w},\vec{x}>+b)]=0 \ \forall \ i$$
$$ 0 \leq \alpha_i \leq C \ \forall i$$
* An hard margin SVM corresponds, as said before, to a soft margin SVM with $C=\infty$, and so with $\alpha^i$ without any upper bound

## Kernels
* I cannot use a linear SVM to solve non linearly separable problems
* I can map the original input space to a linearly separable feature space, which I can solve with SVMs
* In general I do not want to craft a feature space that is specific to the problem, but I can apply some general concepts
* Increasing the dimensionality of the input space increases the number of hyperplanes and thus the likelyhood of linear separability
* The input vector $\vec{x} \in \mathbb{R}$ is transformed to the feature vector $\vec{\phi}(\vec{x}) \in \mathbb{R}$
* Computing the transformation can be costly since the feature space can have a very high number of dimensions (even infinite!)
* The kernel trick makes instead an equivalent computation with a really small computational cost
	* Let's recall the SVM Dual Lagrangian
$$\mathcal{\bar{L}}(\alpha^i) = -\frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j <\vec{x}^i,\vec{x}^j> + \sum_i \alpha^i$$
	* The data points appear only as a scalar product $<\vec{x}^i,\vec{x}^j>$
	* If I am able to calculate just the scalar product in the feature space, I do not need to define that space explicitly in order to use it for the SVM
	* Many common geometric operations can be expressed in terms of scalar product of vectors
* A kernel $K$ is a function of 2 input points $\vec{x}_i$,$\vec{x}_j$ that replaces the scalar product in the SVM objective function, to implicitly implement a translation of the input to the feature space
$$ K(\vec{x}_i,\vec{x}_j)=<\vec{\phi}(\vec{x}_i),\vec{\phi}(\vec{x}_j)>$$
* Let's suppose that my feature space is defined as
$$\phi(\vec{x})=\phi(\begin{pmatrix} x_1 \\ x_2 \end{pmatrix})=\begin{pmatrix}1 \\ \sqrt{2} x_1 \\ \sqrt{2} x_2 \\ x_1^2 \\ x_2^2 \\ \sqrt{2}x_1x_2 \end{pmatrix}$$
* A scalar product in this space is
$$K(\vec{x}_i,\vec{x}_j)=<\phi(\vec{x}_i),\phi(\vec{x}_j)>$$
$$K(\vec{x}_i,\vec{x}_j)=
\begin{pmatrix}1 \\ \sqrt{2} {x_1}_i \\ \sqrt{2} {x_2}_i \\ {x_1}_i^2 \\ {x_2}_i^2 \\ \sqrt{2}{x_1}_i{x_2}_i \end{pmatrix}
\begin{pmatrix}1 \\ \sqrt{2} {x_1}_j \\ \sqrt{2} {x_2}_j \\ {x_1}_j^2 \\ {x_2}_j^2 \\ \sqrt{2}{x_1}_j{x_2}_j \end{pmatrix}$$
$$K(\vec{x}_i,\vec{x}_j)= 1 + 2{x_1}_i{x_1}_j + 2{x_2}_i{x_2}_j + {x_1}_i^2{x_1}_j^2 + {x_2}_i^2{x_2}_j^2 + 2{x_1}_i{x_1}_j{x_2}_i{x_2}_j$$
$$K(\vec{x}_i,\vec{x}_j)= (1 + {x_1}_i{x_1}_j + {x_2}_i{x_2}_j)^2$$
* The use of the kernel function instead of explicitly defining the feature space is the kernel trick
* In general, given a mapping $\vec{x} \to \phi(\vec{x})$ its kernel $K(\vec{x}_i,\vec{x}_j)$ is defined as the sum of the product of all the components of the feature space
$$K(\vec{x}_i,\vec{x}_j) = \sum_k \phi_k(\vec{x}_i),\phi_k(\vec{x}_j)$$
* A kernel must be symmetric and satisfy some conditions that we did not see in detail (Mercer's condition)
* In the SVM Dual Lagrangian, I can just substitute all the scalar products with kernels in training and classification
$$\mathcal{\bar{L}}(\alpha^i) = -\frac{1}{2}\sum_i \sum_j \alpha^i \alpha^j y^i y^j K(\vec{x}^i,\vec{x}^j) + \sum_i \alpha^i$$
* Many different functions can work as kernels
* A kernel is actually just a measure of similarity between 2 objects (usually vectors)
* I am not restricted to use a vector as input for a kernel
* However, in bioinformatics it is not very useful to use non-standard kernels
* Kernels are not only used for SVM, they can be used wherever only scalar products need to be defined
	* They are also used in PCA and other classification techniques
* A stationary kernel is defined in terms of a difference between inputs
$$K(x_i,x_j)=k(\vec{x}^i-\vec{x}^j)$$
	* It is called stationary since it is invariant to translations of the input space
* A radial basis function kernel (or homogeneous kernel) measure the euclidean distance among points
$$K(\vec{x}^i,\vec{x}^j)=k(||\vec{x}^i-\vec{x}^j||)$$
* The homogeneous polynomial kernel of degree d is defined as
$$ K(\vec{x}^i,\vec{x}^j)=(<\vec{x}^i \vec{x}^j>)^d$$
	* This kernel includes all (and only) the possible expansions of degree $d$ of the vector components
	* The number of dimensions for an homogeneous polynomial kernel of grade $d$ with an input space $\mathbb{R}^n$ is
$$\frac{(n+d)!}{n!d!}$$
	* This grows as $~ n^d$ for $n >> d$
* The classic SVM without kernel can be seen as an homogeneous polynomial kernel of degree $1$
$$ K(\vec{x}^i,\vec{x}^j)=<\vec{x}^i,\vec{x}^j>$$
* The non-homogeneus polynomial kernel is defiend as
$$ K(\vec{x}^i,\vec{x}^j)=(1+<\vec{x}^i,\vec{x}^j>)^d$$
	* This kernel is more widely adopted since it includes all the possible combinations of degree up to $d$ (it has many more dimensions!)
	* Also here the number of dimension grows like $n^d$
* The degree of the polynomial kernel influences the likelyhood of overfitting the data
	* An high degree polynomial tends to increase the number of support vectors
	* This is because the curve tends to fit the data as well as possible
	* A way to limit overfitting is to assure that the number of support vectors is much smaller than the total number of points
* The RBF (Radial Basis Function) or gaussian kernel is defined as
$$K(\vec{x}^i,\vec{x}^j) = exp(\frac{(|\vec{x}^i-\vec{x}^j|)^2}{2\sigma^2}) = exp(-\beta (|\vec{x}^i-\vec{x}^j|)^2)$$
	* It can be viewed as a generalization of a polynomial kernel with infinite degree
	* This is because an exponential can be approximated by an infintite polynomial sum
$$exp(x) = \sum_{n=0}^\infty \frac{x^n}{n!}$$
	* Small polynomial degrees have a large weight, while high degree ones have less weight
	* The value of the kernel is big when the difference between $\vec{x}^i,\vec{x}^j$ is big, and tends rapidly to 0 otherwise
	* The hyperparameter beta (or sigma) determines the width of the curve
	* They determine the scale of the diffenrence among points that is considered significant for the kernel
	* A small sigma creates a more complex hyperplane
	* Whith extremely small sigmas, all the points become support vectors
	* A large sigma tends to a linear discrimination
* New kernels can be defined from the linear combination, product, exponential, polynomial transformation, and function of existing kernels
* The Spectral kernel uses sequence similarity as a measure
	* In general, non-vector kernels are not so effective, but they are an intriguing
* The choice of the kernel is the most tricky part of SVMs
* In general, I start from a low-degree polynomial kernel or RBF with large sigma

## Final Remarks on SVM for Classification
* In general, SVMs do not provide a confidence level on the classification
* I can interpret the SVM discriminant function as a probability by performing logistic regression on the SVM output of a validation set
* SVMs are easy to train and provide global optima, differently from NNs
* I can control explicitly the tradeoff between complexity and error
* The main problem of SVMs is that they are heavily dependent on the kernel choosen

# Regression
* A regression is an analysis of several variables where the focus is on the relationship between a dependent variable and one or more independent variables
* I want to interpolate the data with a continuous function of the independent variable(s)
	* It is possible to do regression also with non-continuous functions, but you need to have particular reasons to do so
* Classification can be seen as a regression with a discontinuous function

## Linear Regression
* A linear regression is a line $y = ax+b$ that minimizes some measure of error wrt the datapoints
* A training point $y_i$ can be defined in term of the interpolating line as
$$ax_i+b+\epsilon_i$$
	* $\epsilon_i$ is the error relative to that point
* A common error metric is the least sum of squared distances from the line
* With the least squares, the error function is
$E = \sum_i \epsilon_i^2 = \sum_i [y_i-(ax_i+b)]^2$
* The partial derivative of the error function wrt to b is 0 when
$$\frac{\partial E}{\partial b}=0$$
$$b = y^*-ax^*$$
* While with respect to a
$$\frac{\partial E}{\partial a}=0$$
$$ a = \frac{cov(x,y)}{\sigma_x^2}$$

## Polynomial Regression
* I can use a polynomial to interpolate my points in the form
$$y=P(x)=\sum_{k=1}^p a_kx^k+b$$
* $p$ is the degree of the polynomial and $a_k$ the trainable parameters
* The error function is
$$E=\sum_i (y^i-P(x))^2$$
	* Here $P(x)$ incorporates all the coefficients $a_k$ and $b$
* I can find the solution of the optimization by equating to 0 all the partial derivatives of the error function with respect to the parameters

## Regularization
* Having an high number of parameters leds to overfitting
* A typical sign of overfitting is the presence of coefficient which are very large or very negative
* Introducing a regularazing term in the error function discourages the presence of coefficients with very large absolute value
* The regularized error function for a polynomial regression is thus
$$E=\sum_i (y^i-P(x))^2 + \lambda \sum_k a_k^2$$
	* $\lambda$ is an hyperparameter that tweaks how heavily the model penalizes large coefficients

## Neural Networks for Regression
* The classification error function for NN is
$$E=\frac{1}{2}\sum_{i,j}(z_j(x^i,\vec{w})-y^i_j)^2$$
	* $i$ iterates through the training examples
	* $j$ iterates through the output neurons
	* $z_j$ represents the output of one of the output neurons
	* $\vec{w}$ is a vector of weights
	* $y^i_j$ is the correct value of output neuron $j$ for input $i$
		* In a classification problem it is either 0 or 1
* In a regression problem nothing really changes, I just make $y_i^j$ be a real number instead of 0 or 1
* Also for NN it is useful to introduce a regularizing hyperparameter on the value of the weights

## Support Vector Machines for Regression
* The situation here is less straightforward than for NNs
* Suppose that I have a point $\vec{x}^i \in \mathbb{R}^n$ associated to the point $y^i \in \mathbb{R}$
	* Note that in this case $y^i$ is a real number, not only 1 or -1 like for the classification case
* I define a function $f(\vec{x}) \in \mathbb{R}$
$$f(\vec{x}^i)=w_1x_1+w_2x_2+...+w_nx_n$$
$$f(\vec{x})=<\vec{w},\vec{x}>+b$$
	* Note that this is NOT an hyperplane but a function of the vector $\vec{x}$ that produces a real number!
	* This function is a line in the real space
* I introduce the hyperparameter $\epsilon$ that defines what is the error that I allow on the regression
	* It is the maximum allowed distance from the line to any of the training points
	* It is similar to a margin, but it is an hyperparameter!
* So my goal is to find a line that respect the condition $|y^i-f(\vec{x}^i) \leq \epsilon$
* This constraint can be summarised, removing the absolute value, as
$$\begin{cases}
y^i-(<\vec{w},\vec{x}^i>+b) \leq \epsilon\\
(<\vec{w},\vec{x}^i>+b)-y^i \leq \epsilon
\end{cases}$$
* Among all the lines that respect this constraint I choose the one that minimizes $\frac{1}{2}|\vec{w}|^2$
	* Minimizing the norm of $\vec{w}$ here corresponds to a regularization parameter
	* The components of $\vec{w}$ are the coefficients of the regression, so minimizing the norm of $\vec{w}$ I minimize the value of the coefficients
	* In practice, with this formulation the SVM will choose the line that is as flat as possible
* Also for regression it is possible to implement a soft margin
	* I introduce 2 slack variables $\zeta$ and $\zeta^*$, one for the points above and one for the points below the line
	* The slack variables allow some points to exceed the distance of $\epsilon$ from the line
* I can then obtain as usual the Lagrangian, write the KKT conditions and obtain the Dual Lagrangian
* The SVM Dual Lagrangian used for regression is a bit more complex than the one used for classification but still depends on the data only by a scalar product
* This means that I can use kernels also for regression with SVMs
* Using kernels with SVMs I can do a non-linear regression
* The kernels used are the same used for classification: polynomial and RBF
* Predicting new points with regression SVMs also requires only scalar products, and so I can use kernels also here
* The important thing to remember from SVM regression is that it is a method that incorporates automatically a regularization, and that the allowed error $\epsilon$ is an hyperparameter
* A small $\epsilon$ leads to overfitting since it effectively neutralizes the regularization
	* It is not possible to find a solution that keeps the points inside the margin with a small $\epsilon$
* It is possible also to define different penalty function for the slack variables
	* We used the $\epsilon$-insensitive but there are many others

# Decision Trees

## Decision Trees for Classification
* Decision trees were invented twice, once by statisticians and once by the AI community
* A tree is a set of decisions that determine which variables to consider at each step, and the outcome of each decision until we reach a leaf with an output category
	* Each internal node tests an attribute of the data
	* Each branch corresponds to an attribute value
	* Each leaf corresponds to an output category
	* Different branches are allowed to have different depths
* At each decision step, the data table is reduced and can be used to train lower levels of the network
* Decisions in a tree can be easily implemented with if...else statements
	* They are disjunctions of conjunctions of constraint on the attribute value instances
* It is possible to represent the same set of conditions with a different tree
	* In general I want to select the simplest tree that can represent a given set of conditions
* Training a tree means to minimize the number of misclassification errors, while maximizing its simplicity
* It is almost always possible to build a perfectly discriminating tree, but at the cost of having a very high number of decisions
	* In case of ambiguous examples, it is not possible to create a perfect tree, no matter the number of decisions
	* Ambiguous examples are 2 training points with the same input variables but with different output variables
* The naif approach to create a tree is to create a path for each example
	* This is trivial but not useful
	* I am just memorizing the training examples, without learning anything
* In the Top-Down Induction on Decision Trees (TDIDT) I proceed as follows
	* The current table or sub-table is called Learning Sample (LS)
	* If all the objects in the LS are in the same class
		* Create a leaf with that class
	* Else
		* Find the best splitting attribute A
		* Create a node for the attribute A
		* For each value of A
			* I create a sub-table LS for data with that value
			* I iterate the algorithm in that LS
* TDIDT is an hill-climbing algorithm in the space of possible decision trees
	* It adds a sub-tree to the current tree and continues
	* It never backtracks
* TDIDT is very fast but sub-optimal and highly dependent on the criteria used for the selection of the best attribute
	* It is however the most used approach
* DTs are used in random forests, where no single tree needs to be optimal
	* In a sense actually I want some noise in a tree
* When deciding the best attribute for a split, I want to maximize the purity of the split
	* The purity of a split is a measure of how pure (belonging to the same class) each successor of a split is
	* By maximizing purity, I minimise the height of the tree
* I can define an impurity measure $I$ on a learning set $LS$ such that
	* Let $p_j$ be the proportion of samples in $LS$ of class $j=1,...,J$
	* $I(LS)$ is minimal when all the objects in $LS$ belong to the same output class $i$
$$ p_i = 1 \land p_j = 0 \ \forall\ j\not=i$$
		* It is certain that an object belongs to class $i$ ($p_i=1$) and impossible that it belongs to any class $j$ different from $i$ ($p_j=0\ \forall\ j\not=i$)
	* $I(LS)$ is maximal when the probability of an object to belong to each of the possible classes is equal
$$ p_j = \frac{1}{J} \ \forall \ j$$
	* $I(LS)$ is symmetric with respect to all classes $j=1,...,J$
* The best split of a $LS$ is the one that maximizes the expected reduction of impurity $\Delta I$
$$ argmax_A(\Delta I (LS,A))\ ; \qquad\Delta I (LS,A) = I(LS) - \sum_a \frac{|LS_a|}{|LS|}I(LS_a)$$
	* $\Delta I$ is defined for each attribute $A$, with possible attribute values $a$
	* $LS_a$ is the subset of the $LS$ with value $a$ for the attribute $A$
	* $\Delta I$ is called score measure or splitting criterion
	* The best split is the one on the attribute $A$ that maximises the reduction in impurity of the $LS$
	* The impurity of each of the resulting splits is weighted on the number of training samples involved
* I can define the impurity of a $LS$ in term of its information (Shannon's) entropy
$$H(LS)=-\sum_j p_j \log_2 p_j$$
	* The reduction in entropy is called information gain
* Other possible measures of impurity are
	* The Gini Index, which is similar to the Shannon's entropy
$$I(LS) = \sum_j p_j (1-p_j)=\sum_{j\not=k}p_jp_k$$
	* The misclassification error rate
$$I(LS) = 1-max_j(p_j)$$
* Trees tend to be quite unstable (high variance) and not so competitive compared to other approaches
* A tree $T$ is overfitting the training data if exists a tree $T'$ such that the error of $T$ on the training set is lower than that of $T'$, but the error on unseen data is lower for $T'$
* Overfitting happens when I do not have enough data in some parts of the learning sample to make a good decision
* Overfitting in DT can be avoided by using pre- or post-pruning, or ensemble methods
* In pre-pruning I proceed with TDIDT as usual but I stop splitting a node if
	* The number of object in the node is under a threshold
	* The impurity of the $LS$ is under a threshold
	* The classification improvement of an additional split is not significant according to some test
* The main limitation of pre-pruning is that the value of the thresholds are problem-dependent
* Pre-pruning is normally used by default with very permissinve parameters so to avoid clearly unnecessary work
* In post-pruning I allow the tree to grow (eventually with a very permissive pre-pruning) and then remove some of the nodes
	* I split the original learning sample $LS$ in a growing sample $GS$ and a validation sample $VS$
	* I build a complete tree (or I use permissive pre-pruning) from $GS$
	* I compute a sequence of trees $\{T_1,T_2,...\}$ where
		* $T_1$ is the complete tree (or pre-pruned tree)
		* $T_i$ is obtained by collapsing some nodes in $T_{i-1}$
	* I select the tree $T_i^*$ from this sequence that minimizes the error on $VS$
* If I have a large dataset, I split it into training, validation, and testing sets and use them as usual in ML
* If my dataset is limited, I grow a tree from the whole dataset and
	* I pre-prune with default parameters (this is risky, I can skip an optimum)
	* I post-prune by 10-fold cross-validation
	* I estimate the accuracy by 10-fold cross-validation
* DTs can deal easily with continuous attributes
	* I can discretize them in bins before growing the tree
	* I can use a threshold as decision parameter in the tree itself
* In order to find the best cut-point for a continuous attribute, I can try a range of values and select the one that produces the purest split
* In DTs, it is advisable to use always binary splits, even for attributes that have more than 2 values (by gruping them!)
* When there are missing data, I can deal with them in different ways
	* I can assign to the missing point the most common value for the attribute in the whole dataset
	* I can assign to the missing point the most common value for the attribute in the current $LS$
	* I can assing a probability to each possible value

## Decision Trees for Regression
* The concept is the same used for classification, but each leaf contains a number instead of a class
* A regression tree is a piecewise constant function of the input attributes
* The assigned to a leaf is average output of the learning cases that reach that leaf
* The impurity of a sample is defined as the vaiance of the output of that sample
$$I(LS) = var_{y|LS}\{y\}=E_{y|LS}\{(y-E_{y|LS}\{y\})^2\}$$
	* Since the output for a leaf is the mean of the training values falling under it, the mean squared distance with respect to the mean is the variance of the sample
	* Thus, the variance is a measure of the error, or impurity, of the $LS$
* The best split is the one that reduces the most the variance
$$\Delta I(LS,A) = var_{y|LS}\{y\}-\sum_a\frac{|LS_a|}{|LS|}var_{y|LS_a}\{y\}$$
* Also in regression we can use pre- and post-pruning
* In post-pruning, we select the tree that minimizes the squared error on $VS$
* Pruning is very important in regression trees since they tend to be very complex

## Final Remarks
* The main advantage of decision trees is their interpretability (they are white boxes)
	* If an attribute is not important, it will be pruned from the tree
	* Removing the dependency on attributes can be important of some attributes are costly to measure
* DTs are often used as a pre-processing step for removing irrelevant attributes for algorithms that are more sensitive to irrelevant variables
* The importance of variables can be computed from the total reduction in impurity broght by each variable
$$ Importance(A) = \sum_{nodes\ where\ A\ is\ tested}|LS_{node}|\Delta I(LS_{node},A)$$


# Ensemble Methods
* Ensemble methods predict class label for unseen data by aggregating a set of independent predictions
* Good questions for ensamble predictors are the ones for which I can expect that all the single predictors have the same likelihood of giving the right answer
* A bad question for an ensemble method is a question that requires specialised knowledge
* The main disadvantage of ensemble methods is that they are typically black boxes
* I have $N$ single binary classifiers, each with an error $\epsilon$, and I apply a majority rule
	* In order to obtain a wrong answer from the ensamble, the majority of individual classifiers must give a wrong answer
	* The probability that this happes is given by the binomial distribution
$$P = \sum_{k=N/2+1}^{N} {N \choose k} \epsilon^k(1-\epsilon)^{N-k}$$
	* Note: this is true only for INDEPENDENT classifiers!
	* If I assume that $N=25$ and that the error is $\epsilon = 0.35$ (wrong answer 35% of the times), the ensamble has an error rate of $\epsilon=0.06$!
* Let $C_i$ be the i-th of M classifiers, its square error with repsect to the desired output $o(x)$ for the examples x is
$$\epsilon_i = \langle (C_i(x)-o(x))^2 \rangle_x$$
	* The angle brackets indicate the mean over the x samples
* I define the average error of the a classifier
$$\bar{\epsilon}=\frac{1}{M}\sum_{i=1}^M\epsilon_i$$
* Let $H$ be the ensemble classifier, with all the $M$ classifiers have a weight of $\frac{1}{M}$ each on its outcome
$$H(x)=\frac{1}{M}\sum_{i=1}^MC_i(x)$$
* The error of the ensemble method is the squared difference of the ensemble prediction from the desired outcome
$$\epsilon_H = \langle (H(x)-o(x))^2 \rangle_x$$
* It can be derived that the error of an ensemble method is the average error of the classifiers minus the variance of the classifier predictions with respect to the ensemble method
$$\epsilon_H = \bar{\epsilon}-\frac{1}{M}\sum_{i=1}^M \langle(C_i(x)-H(x))^2)\rangle_x$$
	* The squared distances from the ensemble prediciton are necessarily positive, so $\epsilon_H \leq \bar{\epsilon}$
	* The improvement of ensemble methods is high when classifiers are very dissimilar but of similar accuracy

## Bootstrap AGGregatING (BAGGING)
* Bootstrapping is resampling with replacement
* Bagging reduces the variance of predictors by voting or averaging across bootstraps
	* In some situations it could also decresase the perfromances
	* Usually, the more classifiers I use the better
	* It is really useful for noisy data
* In the training procedure, I resample the dataset $S$ with replacement and create a number of bootstraps $S_i$, with which I train a number of classifiers $C_i$
* For classificating an unknown example $x$, I assign to it the class predicted by the majority of individual classifiers
* Bagging can be used for regression by taking as an ensemble output the average of all the predictions
* If small changes in the training set cause large changes in the learned classifier, the training algorithm of that kind of classifier is said to be unstable
* Bagging is really effective with unstable learning algorithms: decision trees, linear regression, SVM, ...

## Random Forests
* Another approach similar to bagging is to randomize the learning algorithm instead of the input data
	* Some algorithms already feature a random component (initiation point of gradient descent)
	* Most algorithms can be randomized by picking one of the best options at random intead of the absolute best at each step, or by inserting randomness in the split rule of decision trees
* Random Forests (RF) are a combination of decision trees trained with bagging
	* The dataset is resampled with replacement, and individual trees are trained for each replicate
	* Single tree splits are choosen randomly from a set of the best features, instead than from the absolute best
	* Ensamble decisions are taken by majority voting
	* No post-pruning (and occasionally only very little pre-pruning) is used on the trees, since overfitting is dealed with by the ensamble
* The probability that a training example is extracted $k$ times in one bagging process can be derived from the binomial distribution
$$p(k) = {m \choose k} (\frac{1}{M})^k (1-\frac{1}{M})^{m-k}$$
* So the proabability that a sample is never extracted ($k=0$) is
$$p(0) = {m \choose 0} (\frac{1}{M})^0 (1-\frac{1}{M})^{m}$$
$$p(0) = (1-\frac{1}{M})^{m}$$
* In the case that the bootstrap datasets have the same size of the original one ($m=M$) I have that
$$p(0) = (1-\frac{1}{M})^{M}$$
$$\lim_{M \to \infty} p(0) = \frac{1}{e}\approx \frac{1}{3}$$
* The examples that are not selected in a single bagging are called out of bag (oob) examples, and they tend to be around a third of the training points for large datasets
* Since oob examples are not used in the training of the single tree, they can be used for validation
* I can use the oob examples for obtaining the oob error estimate
	* I train a tree $T_i$ with the bootstrap dataset $S_i$, and then estimate its error against the oob examples
	* This will give a performance metric on about a third of the trees
	* At the end of the run, let $j$ be the class that got the most votes every time the example $n$ was oob
	* The fraction of times that $j$ was not the true class of $n$, averaged over all the oob examples, is the oob error estimate
* It is argued that the oob error estimate can be used in place of a testing set, but this is strongly disputed
* It is possible also to estimate variable importance from oob errors
	* I evaluate the oob error as usual
	* I permute randomly the variable $i$ in the oob cases
	* I subtract the fraction of correct votes in the permutated sample from the oob error
	* The average over all the trees is the raw importance for variable $i$

# Systems Biology
* A system consists of many distinguishable parts that strongly interact with each other, and can also interact (weakly or in a different way) with the surrounding environment
* A system is a set of interacting entities forming an integrated whole
* Systems have a structure, defined by their parts and their composition
* Systems have a behaviour, which involves inputs and outputs of material, energy, or information
* Systems have interconnectivity: the various components have functional and structural relationships to each other
* Systems can exhibit emergent properties
* Laplace's deamon: the universe is deterministic and, given complete knowledge of its state, can be predicted in the past and in the future
* Prediction is very difficult, especially about the future (Niels Bohr)
* For Weaver, the complexity of a system is the degree of difficulty in predicting the properties of that system from the properties of its parts
* Complexity is not related to the entropy of the system
* Gas systems can be described in terms of the componing molecules
	* Statistical mechanics reduces thermodynamics to classical mechanics
	* Emergent properties of a gas (not belonging to single molecules) are temperature and pressure
	* The theory of gasses requires disorganized complexity
* The pattern of interactions in a complex system is not random but also not regular
* For Weaver, there is disorganized complexity and organized complexity
* Disorganized complexity refers to a problem in which there is a very large number of variables, each behaving erraticaly or in an unknown way, but that collectively define well-quantifiable and predictable average properties
* Organized complexity problems involve a large number of factors interrelated into a organic whole
* Complexity is not only due to the number of parts: 3-body problem
	* Poincaré showed that there is no analytical solution of the 3-body problem
	* The motion is in general not-repeating, except in special cases
	* A complex system is a system that is difficult to predict
* Non-linear terms in interactions lead to complex effects
	* Systems composed of few parts can lead to symmetry breaking and deterministic chaos
* Symmetry breaking is a phenomenon where small fluctuations on a system cross a critical point and decide the system's fate
	* It is supposed to play a major role in pattern formation
* Ferromagnetism is an example of symmetry-breaking
	* The symmetry in question is the up-down symmetry
	* The breaking happens with the formation of magnetic domains containing aligned magnetic moments
	* As temperature increases, thermal motion scrambles the aligned domains
	* Above the Curie temperature of the material, thermal motion overpowers the alignment of the domains and symmetry breaking does not occur+r
* Polya's urn is also an example of symmetry breaking
	* An urn contains a red ball and a green ball
	* A ball is extracted, and 2 balls of the same colour are returned to the urn
	* After some iterations, most of the balls tend to be of a single color, randomly selected according to the frist few iterations
	* The system is governed by positive feedback
* Determininstic chaos refers to a system of elementary units governed by non-linear laws, which exhibits an extreme dependence on initial conditions
	* The system is deterministic but its evolution is unpredictable
	* Non-linarity is necessary for deterministic chaos
* Systems that are not at equilibrium tend to behave chaotically
	* The atmosphere is similar to gas in a chamber, but it behaves chaotically since there is a continuous influx of energy that maintains it far from equilibrium
	* Non-equilibrium systems can lead to self-organizing behaviours: convection cells in fluids
* Complex systems can be open and dissipate energy ($\frac{dE}{dt} > 0$)
* Complex systems can have memory effects in their responses
* Complex systems can be nested and without precise boundaries
* Non-linearity is present also in many chemical reactions (law of mass action)
$$A+A \underset{k_2}{\stackrel{k_1}{\rightleftharpoons}} B$$
$$ \frac{d[B]}{dt} = k_1 [A]^2$$
* Biology is described by genotype and phenotype
	* The final goal of the life sciences is always the phenotype
	* The main aim of systems biology is to reconstruct the phenotype from the genotype
* Reductionism is the approch to reduce the nature of complex things by describing them in terms of the interactions of their parts
	* Reducing a system is not possible when there is deterministic chaos or symmetry breaking, since it is not possible to know anything with infinite precision, since it is not possible to know anything with infinite precision, since it is not possible to know anything with infinite precision
	* Ontological reductionism is the idea that everything is composed of matter and energy
	* This is generally accepted
* Methodological reductionism builds on top of ontological reductionism, assuming it
	* It postulates that the best level for studying  biological systems is that of atoms and molecules
	* This is debated, since some properties of systems are hard or impossible to investigate at the level of individual components
* Epistemic reductionism postulates that all science is either physiscs or stamp collecting (Rutheford)
	* This is not generally accepted
	* "At each stage, entirely new laws, concepts and generalizations are necessary, requiring inspiration and creativity to just as great a degree as in the previous one. Psychology is not applied biology nor is biology applied chemistry" (Anderson, More is Different)
* More is different: emergent properties
	* Emergence can be defined as the arising of novel and coherent structures, patterns and properties during the process of self-organization in complex systems (Corning, 2002)
	* Charachteristics of emergent phenomena are radical novelty, coherence, wholeness, they are the product of dynamic processes, and they are ostensive (perceivable)

## Models
* An abstract model is a theoretical construct that represents something, with a set of variables and a set of physical relationships among them
* Models can make wrong assumptions, that can be justified by the fact that they simplify the model while producing acceptable solutions
* A model can be tested with respect to experiments, and it is useful for dissecting which parts of a sistem contribute to a certain property of interest
* Model can be used for hypothesis generation and testing, without actually performing experiments
* Structural models are entities that can be cast as nodes interacting with each other via edges
* Creating a model involves selecting an appropiate level of abstraction
* Biological networks tend to be scale free
* Higher levels of abstraction tend to be less organism-specific and more universal
* Dynamic models require kinetic rate equations to be described
	* They are typically described with Ordinary Differential Equations (ODE)
	* They are much more complex that other models
* Dynamic models focus on how each component influences the rate of change of other components
* They describe a time-varying behaviour
* The Michaelis Menten equation describes the behaviour of enzymatic reactions
$$A \to B$$
$$\frac{dB}{dt}=\frac{v_{max}A}{K_{MM}+A}$$
* A differential equation is an equation for an uknown function of one or several variables that relates the value of the function and that of its derivatives of various order
* ODEs can be solved numerically, and it is possible to study their behaviour using dynamical systems
* We will not solve differential equations, which is complex, but we will try to charactherize their steady states
* An attractor in a differential equation is a stable point where the system tends to fall to, after a transient period
* Differential equations are quite complex since require many parameters (one constant for each derivative in chemical reactions)
* Boolean Networks are qualitative discrete computational models
	* Each molecule in the network is described as either active or inactive
	* They are much simpler than differential equation since they are qualitative and have much less parameters
	* Also in boolean networks it is possible to study the stability of the system, the presence of cycles or attractors
	* A molecule is active if the sum of its activations is larger than the sum of its inhibitions
	* The state of the system is described as the set of active molecules
	* Each state represent a node of a graph, and state transitions are edges
	* Loops are used to deduce stable states, and the number of loops is a measure of robusteness
	* A network state is represented as a boolean vector (of active/inactive molecules)
	$$\vec{x}=(A,B,C)$$
	* A state evolution is represented as a boolean function of the previos state for each molecule
	$$\vec{x}(t+1)=f(\vec{x}(t))=(f_A(\vec{x}(t)),f_B(\vec{x}(t)),f_C(\vec{x}(t)))=(A \lor C, A \land C, (\lnot A) \lor B)$$
		* For example, for $\vec{x}(t)=(0,1,1)$ the evolution is $\vec{x}(t+1)=(1,0,1)$
		* A stable state, called attractor is a state that produces itself after an evolution (a loop!)
		* A cycle is a set of states that in a certain number of evolution repeat themselves
		* This is called descrete synchronous dynamics, since state transitions happen simultaneously to all the molecules through concurrent gate firings
* The replessilator is a boolean loop of three repressors in an cycle
$$\vec{x}(t)=(A,B,C)$$
$$\vec{x}(t+1)=(\lnot C, \lnot A, \lnot B)$$
	* It was implemented for real with a plasmid using TetR, LacI, and $\gamma$cl, which repress each other
	* It is characterised by a small cycle ($000 \leftrightarrow 111$) and a large cylcle including all the remaining states
	* Transitions among the 2 cycles are forbidden
* A Petri Net (Petri, 1962) is a graph with 2 types of nodes: places and transitions
	* The edges connect places to transitions and vice-versa
	* The state of the system is represented by places holding tokens
	* Transitions change the state of the system by moving tokens along edges
	* Petri nets are more quantitative than boolean networks but less demanding than differential equations
* Process Calculi is a quantitative, dense, stochastic computational model
	* It uses languages to model systems
* Models to be useful need to be parametrized
* Excessive parametrization can lead to overfitting
	* This applies only to parameter tuning used for reproducing experimental data with a model
	* This can lead to overfitting the single experiment!
* In some cases parameters are known for a model
	* In this case we can easily predict the evolution of the system with forward modeling
* If parameters are unknown, we need to reverse engeneer the system
	* An analytical solution is often impossible, and so a fitting procedure is used
* Models can be stochastic or deterministic, discrete or continous, macroscopic or microscopic, hierarchical or multi-level, quantitative or qualitative
	* Continuos models can be described by differential equations, discrete models by boolean networks
* The ultimate goal of system's biology is to create a silicon cell, a complete model of a cell and of a human body

## Structural Models
* The main networks that we want to investigate are protein-protein interactions, gene regulation networks, and metabolic networks
* PPIs can be studied via affinity purification, Y2H, and other techniques
	* Affinity purification is mmost suited to detect strong interactions and complexes
	* Y2H is more suited for transient direct interactions
		* Y2H can detect interactions only if they happen in the nucleus!
	* Protein-protein interaction assays tend to be really noisy and not so reproducible
		* There is very little overlap among the proteome determined by different studies
		* The result are very sensitive to conditions and to experimental error
		* One source of error is the presence of indirect (spurious) interactions
	* Because of the low reproducibility, the definition of proteome is fuzzy
	* The main experimental PPI databases are IntAct and BioGRID
		* They report both large-scale and small scale experiments
	* STRING is a meta-database that integrates data from other databases and computational predictions
		* Differentli from IntAct, STRING does not report only physical interactions but also genetic interactions
	* Logical PPIs can be predicted from co-expression data
		* If 2 proteis are always regulated together they probably take part in the same biological process
		* Co-expression is not strong evidence for physical interaction but for logical-biological interaction
	* Protein intractions (physical or not) can be computationally inferred in different ways
		* Genomic profiles
			* In a genomic profile a set of genomes is tested for the presence of a set of proteins, forming a boolean matrix
			* Proteins that tend to appear togheter in genomes could be biologically interacting
			* I need a substantial amounts of genomes to compare for this to be meaningfull
		* Fused or separated
			* The presence of 2 independent proteins in some genomes, which is some other genome are fused together, is a strong indication of the fact that they are physically interacting
		* Correlated mutations among 2 proteins is an indication of physical interaction
* Two genes are said to interact if the protein product of one gene influences the production rate of the protein product of the other
	* This kind of interaction can be analysed with ChipSeq data by looking for the binding of one protein product to the promoter region of the gene it regulates
	* ChipSeq data does not give information on the type of interaction (inhibition or enhancement)!
	* The type of interaction can be estimated from co-expression data (RNA-seq typically or small scale experiment)
	* A small scale experiment can involve genetic engeneering of the organism so to modify the expression of one gene and asses the influence that this has on the expression of the other
	* Differently from PPI networks, trascription networks are directed =(interactions are not symmetric)
* In metabolomic netrowks nodes are represented by metabolites, and enzymes are not represented
	* Metabolomic studies are typically done with MS or NMR
	* Interaction among metabolites is estimated from their covariation in different datasets

### Indirect Correlations
* When analysing correlations, be aware of spurious correlations
	* A spurious correlation is given by an itermediate variable that is correlated to both of the spuriously correlated variables
* Let's suppose that I have a network of interactions of 3 proteins x, y, z, with their correlation coefficients $\rho$
$$ x \iff y \iff z$$
$$\rho_{xy}, \ \rho_{yz}, \ \rho_{xz}$$
* In this example x is correlated to y, and y is correlated to z, but x and z are spuriously correlated
* If x and z are spuoriously correlated thanks to their mutual correlation to y, then their correlation coefficient will be the product of the correlation coefficients of x and z toward y
$$ \rho_{xz}=\rho_{xy}*\rho_{yz}$$
* Given a set of correaltion coefficients among variables, I can detect spurioous correlations as the lowest of the set
	* The product of 2 correlation coefficients is always lower than the coefficents themselves
	* This is because correlation coefficients are in the range 0-1
* The correlation coefficient $\rho$ is related to the covariance
$$ \rho_{xy} = \frac{cov(xy)}{\sigma^2_x}$$
	* Since the denominator of this fraction is the variance of one of the 2 variables, the correlation coefficient is not symmetric! ($\rho_{xy} \neq \rho_{yx}$)
* The covariance is symmetric and the covariance of a variable to itself is the variance of that variable
$$Cov(x,y)=Cov(y,x)$$
$$Cov(x,x)=\sigma^2_x$$
* The covariance matrix $\Sigma$ is a symmetric square matrix of all the possible covariances among a set of variables
$$\Sigma = \begin{bmatrix}
	\sigma^2_x && Cov(x,y) && Cov(x,z)\\
	Cov(y,x) && \sigma^2_y && Cov(y,z)\\
	Cov(z,x) && Cov(z,y) && \sigma^2_z\\
\end{bmatrix}$$
* For complicated reasons in the modelling of the D-dimensional data as normally distributred in a D-dimensional space, a quantity appears that is the invers of the covariance matrix, $\Sigma^{-1}$
* The inverted covariance matrix $\Sigma^{-1}$ is called precision matrix $K$
$$K=\Sigma^{-1}$$
	* In the precision matrix all the non-directly correlated variables will show a coefficent equal to 0
* The partial correlation indexes $\tilde{\rho}$ are another kind of correlation index that can be obtained from the precision matrix
	* The partial correlation indexes show the independent correlation among any pair of variables, independently from the effect of other variables
* I can obtain the partial correlation indexes from the precision matrix $K$ with a simple formula
$$\tilde{\rho}_{x_ix_j}=\frac{-K_{ij}}{\sqrt{K_{ii}K_{jj}}}$$
* The use of partial correlation indexes allows to purify a correlation network from spurious correlations
	* This approach is referred to as gaussian graphical model, precision matrix computation or inversion of the covariance matrix
	* It was initially applied to a metabolomic study
		* After the correction most interactions appeared among metabolite of the same class, as expected, while before the correction there was a large number of significant correaltions
* Gaussian modelling is not perfect, but frequently givesmor reasonable models than the simple correlation coefficents
* This approach can be extended to the study of interactions among residues in the same protein so to predict contact maps
	* Even a 30% of correct contacts can give a reasonable ab initio prediction of protein structure
	* The main limit is that I need really a lot of proteins to compare in order to study covariation of residues (many thousands)

## Networks
* A network is a mathematical entity composed of nodes and edges
* Edges can be direct or indirect, weighted or not
* Each node is characterized by an in-degree and an out-degree
* An Eulerian path in a network is a path that passe for each edge exactly once
	* It is possible only if there are 0 or 2 nodes of odd degree
	* The only way to have an Eulerian path with nodes with an odd number of edges is to use them as starting and end points, and I can have only 1 starting and 1 end point!
	* It was discovered by Euler by studying the problem of the 7 bridges of Könisberg
* An Hamiltonian path touches each node in a network exactly once
* The centrality of a node is its importance for the connectiveness of a network
* The shortest path among 2 nodes is the one involving the least number of edges (or the least total weight for weighted networks)
* The average shortest path is a measure of the proximity among any pair of nodes in a network
	* This relates to the 6 degrees of freedom in social networks
	* The small shortest path also in large network gives rise to the small-world property of many networks
* The clustering coefficient of a networks measure the local connectivity of the network
	* It is the extent to which the neighbors of a node are connected to each other
* The single-source shortest path can be obtained with the Djkstra algorithm
* The clustering coefficient of a node can be computed as follows
	* I enumerate the neighbors of the node
	* I count the theoretical number of possible connections among the neighbors and the connections among them that are actually present
	* The clustering coefficient of the node is that ratio among the number of connections among its neighbours and the maximum number of possible connections
	* It can vary from 0 to 1
	* In a fully connected network the clustering coefficient of all the nodes is 1
	* Also the clustering coeffcient is a measure of centrality
* I can evaluate also the clustering coefficient of an entire network by averaging the clustering coefficient of single nodes
* A fully connected network is called clique
* Other intereseting features of networks are the distribution of shortest paths and clustering coeffcients

### Regular and Random Networks
* A regular network is a set of nodes connected with regular topologies (a latice)
	* They are easy to analyze and study
	* The clustering coefficent tends to be high
	* The shortest path is high, on the order of $N$
	* The degree distribution is represented by a single value, equal for all the nodes
* A random network is a set of nodes connected randomly
	* They are hard to treat, and result on random networks were mostly proven by Erdös
	* The clustering coefficent tends to be low
	* The shortest path is low, on the order of $\log{N}$
	* The degree distribution is Poisson (exponential decay)
		* There is a small probability (exponentially decreasing) of finding hubs
		* Of course the network is random, so any given netwrok can have a different distribution, but on average they tend to the Poisson model

### Real Netoworks: Small-world and Scale-free
* Real networks tend to be neither regular, nor random
	* Strogats (inventor of small world networks) analysed different networks and compared the parameters measured on those network with the ones theoretically derived by assuming regular and random networks
	* Shortest paths tend to be small, more similar to random networks
	* The clusetring coefficient tends to be high, similar to regular netwokrs
	* Real networks tend to be small world networks: they have high local structure but connection among different clusters make the average shortest path similar ot that of random networks
* Strogatz showed that small world networks can be obtained from regular networks by randomly rewiring some edges (or adding random edges)
	* Depending on the rewiring probability, I can remain in the regular network case, end up in a random network, or for intermediate rewiring probabilities I can get a small-world network
* Strogatz networks have a Poisson-like degree distribution, similar to random networks
* In real networks instead of an exponential decay the degree distribution teends to show a more gentle power-law decay
$$p(k)=A k^{-d} \qquad 2<d<3$$
	* This allows for the existence of a substantial amount of high-degree hubs
	* Barabasi analysed the links among web pages in a specific domain and showed that the degree distribution of the nodes does not follow a Poisson distribution but a power law with exponent typically between -2 and -3
	* Real networks have hubs!
* Real networks are said to be scale free
	* In random networks I can identify a peak in the degree distribution, usually mear its median, and so I can set a number that describes the network
	* In a pure scale-free network the degree of nodes follows exactly an inverse power law: the average degree does not characterize the distribution, which has no real peak
* Scale-free networks are vulberable to directed attacks to their hubs, but are resilient to random attacks (hubs are rare and so unlikely to be hit)
* Recognizing a power-law decay from an exponential decay in experimental data can be hard in a normal graph, but easy in a log-log graph
	* In a logarithmic graph a power-law decay is a line
* Differently from the degree distribution, the clustering coefficient does not depend from the degree of the node
* Scale-free networks tend to arise spontaneously becasue of preferential attachment
	* Nodes with high degree are more likely to gain new connections
	* The network starts with a few random connections, and then becomes scale-free as it grows
* Metabolic networks tend to be scale-free and directed (even though the reactions are reversible!)
	* Hubs are central metabolites that take part in many reactions
* PPI networks tend to be scale-free
	* Some proteins, called sticky proteins, tend to interact with almost everything in experiments, and it is debated if they are true hubs or artifacts due to the non-physiological experimental setting
	* Hubs are not necessarily biologically more important than non-hubs, but there is a trend for more connected nodes to be more lethal upon deletion
	* The preferential attachment model can be related to PPI networks (explanation by Barabasi)
		* Assume that new proteins evolve by gene duplication
		* The new protein will tend to retain the connections of its ancestor
		* The ancestor is more likely to be already connected to hubs than to low-degree nodes
		* The hubs now has one more protein connected to it
* For Barabasi all the scale-free networks arose for preferential attachment, but this is not necessarily true, and there are other models that try to explain scale-freenes
	* Scale-freenes by itself is not a sufficent cause to assume preferential attachment
	* Many papers of the Barabasi school have the wrong implicit assumption that preferential attachment is acting when scale-freenes is observed
* Trascription networks are network of proteins that influence each other's trascription rate
	* They are directed networks
	* The network is not scale-free for the in-degree but it is for the out-degree
		* Genes are not regulated by an enormous amount of trascription factors
		* Single transcription factors can regulate many genes
	* Preferential attachment has been proposed also here but it is much less convincing than for PPI networks
* Some people don't like Barabasi since they think that he is a little overselling his findings

### Hierarchical Networks
* Hierarchical networks have been also propsed by Barabasi
	* They have a scale-free and small-world behaviour
	* They have hubs, but hubs connect different parts of the network, that would be disconnected without them
	* They are "modular networks"
	* Non hubs have very high clustering coefficient (high local connection)
	* Hubs have low clustering coefficient (they are connected to many nodes from different parts of the network that are not connected to each other)
	* They have the property that the clustering coefficient of a node is some function of its degree (depends on it)
	* The parts that wopuld become disconnected after removal of an hub are called modules or communities
	* Barabasi found hierarchical behaviour in many biological networks
* Many real biological networks are scale-free, small-world and hierarchical
	* Low average shortest path, high clustering, and clustering dependent on the degree of the node
* Modules or communities are sets of nodes that are strongly internally connected but loosely connected to other nodes outside of the set
	* They typically represent groups of entities collaborating on some function
* Motifs are small subgraphs that tend to recur many times in a network
	* If a motif is more recurrent than expected it probably has some functional meaning!

### Centrality and the Identification of Communities
* The centrality of a node can be measured in different ways
	* Degree centrality: the in-degree of a node
	* Betweenness centrality: the fraction of shortest paths in the graph that pass through the node
		* Betweeness centrality can be defined also for edges in a similar way
	* Closeness centrality: the mean shortest path from the node to every other node
* Communities can be identified by removing the edge with the highest centrality until the netwrok is disconnected in sub-networks, which are the communities
	* This is called Girvan Newman algorithm
	* Edge centrality is recalculated at each step in the resulting graph
	* I stop at the first step that makes the netwrok disconnected
	* In large networks this way of computing communities can be computationally expensive
* The identification of communities (community clustering) is important for the detection of functional modules
	* This was applied to PPI networks
	* The function of proteins in a cluster can be studied with an enrichment procedure
		* It is statistical procedure that aims at identifying if a label is overepresented in a set of nodes with respect to the background distribution
		* Typically GO terms are used as labels
	* The Fisher test is an exact statistical test that requires tyhe computation of many factorials, which can lead to overflow errors
	* An enrichment analysis is typically done with a Fisher test
		* The Fisher test is an exact statistical test that requires tyhe computation of many factorials, which can lead to overflow errors
		* If the Fisher test is too demanding computationally it is possible also to use a $\chi^2$ test

### Geometric Networks
* Geomteric Networks were discovered by Natasha Prusley (UCL) 10-15 years ago
* In geometric networks nodes are placed in an Euclidean Space, and their connectivity is determined in terms of distance from other nodes in that space
	* All nodes closer than a thereshold are connected
* The main question is: can I represent a PPI networks in a D-dimensional Euclidean space, such that by choosing an appropriate connection threshold $\epsilon$ proteins are connected only if they are $\epsilon$ close?
	* There are algorithms for embedding a given graph in a metric space
	* It can be not possible to do it in a low-dimensional space
* The quality of the embedding is determined in terms of how many false positive and negative connections it generates
* Since I have false positives and negatives, it is possible to draw a ROC curve as a function of $\epsilon$ for a given D-dimensional space
* The striking observation is that the yeast PPI network and many other real networks can be embedded much better than random networks
* This is interesting since we can endow the proteins with some feature (the dimensions) that could predict the extent of interactions
	* But no one knows what these axes are! 













## Ordinary Differential Equations (ODE)
