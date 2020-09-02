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
	* Training means optimizing the value of the parameters for a set of know examples
* The non trainable parameters of the network are called hyperparameters
	* In the perceptron these are the number of neurons in the input and output layers
