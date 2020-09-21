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

# Random Forest

## Decision Trees
* Decision trees were invented twice, once by statisticians and once by the AI community
* A tree is a set of decisions that determine which variables to consider at each step, and the outcome of each decision until we reach a leaf with an output category
	* Each internal node tests an attribute of the data
	* Each branch corresponds to an attribute value
	* Each leaf corresponds to an output category
	* Different branches are allowed to have different depths
* At each decision step, the data table is reduced and can be used to train lower levels of the network
* Decisions in a tree can be easily implemented with if...else statements
* It is possible to represent the same conditions with a different tree
	* In general I want to select the simplest tree that can represent a given condition
* Training a tree means to minimize the number of misclassification errors, while maximizing its simplicity
* It is almost always possible to build a perfectly discriminating tree, but at the cost of having a very high number of decisions
	* In case of ambiguous examples, it is not possible to create a perfect tree, no matter the number of decisions
	* Ambiguous examples are 2 training points with the same input variables but with different output variables
* The naif approach to create a tree is to create a path for each example
	* This is trivial but not useful
	* I am just memorizing the training examples, without learning anything
* In the top-down Decision Tree induction (TDIDT) I proceed as follows
	* The current table or sub-table is called Learning Sample (LS)
	* If all the objects in the LS are in the same class
		* Create a leaf with that class
	* Else
		* Find the splitting attribute A
		* Create a node for the attribute A
		* For each value of A
			* I create a sub-table LS for data with that value
			* I iterate the algorithm in that LS
* TDIDT is very fast but sub-optimal and highly dependent on the criteria used for the selection of the best attribute
	* This is the most used approach
	* DTs are used in random forests, where no single tree needs to be optimal
	* In a sense actually I want some noise in each tree
* When deciding the best attribute for a split, I want to maximize the purity of the split
* I want the purity of a split to be maximal when all the resulting objects are of the same class
* I want the purity of a split to be minimal when the resulting objects have the same probability to belong to all the classes
* I want the purity to be symmetric with repsect to the various classes
* A possible impurity index is the information entropy
$$S=$$
