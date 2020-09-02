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

# Neural Networks for Binary Classification
* Classificating means finding a line that separates classes of data
* We want to use a line since it is a simple model, and it minimises the risk of overfitting
* A line can be described as $x_1 = ax_2+b$, but this is not the most effcient way
* I can better write a line as $w_1 x_1 + w_2 x_2 + b = 0$, since this is extendable to higher dimensions
* The equation of a plane is $w_1 x_1 +w_2 x_2 +w_3 x_3 +b = 0$
* In general I can write the equation for any linear manifold (hyperplane) $\vec{x} \in \mathbb{R}^n$
$$\vec{w}\vec{x} + b = 0$$
* In this framework $\vec{w}$ and $b$ are the paramters to be trained
	* This holds also for SVM and neural networks
* Mach's bands: perception can be different than signal
	* We can treat a retina neuron as a linear model that given a light intensity outputs a voltage proportional to it
	* Suppose that neurons are laterally connected to each other with inhibitory connections
	* The strenght of inhibition on other neurons is proportional to the potential of the neuron
	* At the boundary the highly active neuron inhibits the less active neuron more
	* On the contrary, the highly active neuron at the boundary is more active than normal neurons of its region since the dark neuron does not inhibit it much
	* Lateral inhibition actually is present in the retina
* Simple elements can engage in complex behaviours when they are widely and specifically connected
	* Knowledge is stored in the topology and in the strenght of the synapses
* A model for an artificial neuron: McCulloch and Pitts
	* A neuron is a computational unit that performs weighted sums of the input signals, computing the activation signal
$$ a = \sum_{i=1}^n w_ix_i - \theta$$
	* In this equation $\theta$ is the activation threshold, $w_i$ the weights and $x_i$ the inputs
	* The activation signal is transformed by a transfer function $g(a)$ to give the output $z$
$$z = g(a)$$
* The activation function can be linear
$$g(a) = ma$$
* The Heaviside (Oliver Heaviside) or unit step function can also be used as an activation function
$$ g(a) = \begin{cases}0 & \mbox{if }a < 0 \\ 1 & \mbox{if } a \geq 0\end{cases}$$
	* It returns 0 for negative inputs and 1 for positive inputs
	* This function has the inconvenience of not being continuous
* A more convenient almost-binary activation function is the sigmoid function
$$g(a)=\frac{1}{1+e^{-a}}$$
* The ReLU function (Rectifying Linear Unit) is continuous but not derivable
$$ g(a) = \begin{cases}0 & \mbox{if }a < 0 \\ ka & \mbox{if } a \geq 0\end{cases}$$
	* It is horizontal until 0 and then becomes linear
	* The angular point ($a=0$) is not derivable
* Activation functions tend to routinely be NOT linear
	* The same variation in the input can give very different variations in the output, depending on the absolute activation level
* The threshold $\theta$ can be neglected in the mathematical model
	* I can replace it with a fictitious neuron always activated ($x=1$) which is connetced with a weight $w=-\theta$
* The topology of the connections among neurons define the network class
* We will only talk about feed-forward networks: the actovation travels only forward
* The simplest network is the perceptron: an input layer and an output layer with only feed-forward connections
$$ z_j = g(\sum_i w_{ij} x_i - \theta_j)$$
* I can implement an OR gate with a perceptron with 2 inputs and 1 output
	* I use a Heaviside activation function
	* Weights are $w_{13}=w_{23}=0.5$ and the threshold is $\theta=0.25$
* With the same topology but different parameters I can implement an AND gate
	* I just change the threshold such that $\theta=0.75$
* Also a NOT(1) can be implemented with the same topology
	* I choose $w_{13}=-0.5$, $w_{23}=0.1$, $\theta=-0.25$
* The weights $w$ are the trainable parameters of the network
	* Training means optimizing the value of the trainable parameters for a set of know examples
* The non trainable parameters of the network are called hyperparameters
	* In the perceptron these are the number of neurons in the input and output layers
* I can train the parameters by starting from random values
* For a given set of parameters $\vec{w}$, I evaluate the output values $z_j$ for a set of examples (training data) $x^k$
* I compare the output with a set of desired outputs for the training set $d^k$
* I can define an error (or loss) function $E$ that represents how well the output $\vec{z_k}$ agrees with the desired output $\vec{d_k}$
* A possible error function is a simple difference
$$ E = \sum_{k,j} (z_j((x_k,w_{j,k})-d_{j,k}) $$
	* This is not a good function since contributions with opposite signs cancel each other
* I can use the absolute values of the differences
$$ E = \sum_{k,j} |(z_j((x_k,w_{j,k}))-d_{j,k})| $$
	* This function is not derivable, and so it does not allow to calculate a gradient
* It is better to use the square of the error
$$ E = \frac{1}{2}\sum_{k,j} (z_j((x_k,w_{j,k}))-d_{j,k})^2 $$
	* The constant factor $\frac{1}{2}$ is useful to simplify a computation later, it does not have a specific meaning
	* This is the most used error function in classical neural networks
* The cross entropy is xxx
* After evaluating my error function, I need to update my parameters accordingly if the error is not below a satisfactory threshold
* I can update the parameters randomly
	* This is used in some approaches, but in general it is not so smart if the parameter space is really large
	* In a perceptron with $n$ input neurons and $m$ output neurons the parameter space is $(n+1)m$ (weights plus the thresholds)
		* I have $nm$ weights and $m$ thresholds
* The error function is a function
$$ E_{\vec{w},\theta} : \mathbb{R}^{(n+1)m} \to \mathbb{R}$$
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
* A gradient is a vector containing all the first order partial derivatives of a function
$$ \nabla f(x)= (\frac{\partial f}{\partial x_1},\frac{\partial f}{\partial x_2},...,\frac{\partial f}{\partial x_n})$$
* A function with 2 to inputs and 1 output can be represented with contour lines* The gradient is always perpendicular to the level curves and points always in the direction where the function is increasing

