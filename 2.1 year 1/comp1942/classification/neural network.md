#### Neural Network  
- A computing system made up of simple and highly interconnected processing elements  

##### Other terminologies:  
- Connectionist Models  
- Parallel distributed processing models (PDP)  
- Artificial Neural Networks  
- Computational Neural Networks  
- Neurocomputers

As a simulation of brain where neurons are the main location of information processing.
Interneuron connection strengths known as synaptic weights are used to store the knowledge

##### Advantages of Neural Network
1. Parallel processing
>each neuron work individually
3. Fault tolerance
>whole system works regardless of the break down of units with a degraded performance

Neural network for OR
![[Pasted image 20220416230901.png]]
![[Pasted image 20220416231025.png]]

Activation Functions
- [[Threshold function_step function_Hard limiter]]
- [[Linear function_identity function]]
- [[Rectifier function_Retified Linear Unit_ReLU]]
- [[Sigmoid function]]
- [[tanh function]]

##### Learning
Let $\alpha$ be the learning rate.
$$net=w_1x+w_2x+b$$
$$w_i+\alpha(d-y)x_i\to w_i$$
$$b+\alpha(d-y) \to b$$
d=desired output
y=output of our neural network
w=weight of the net
x=input of our neural network
![[Pasted image 20220417002849.png]]
repeat the process until the neural network output the correct values.

However, it can only solve linearly separable problems.
![[Pasted image 20220417003133.png]]
the third case cannot be solved.

Thus, [[multi-layer perceptron]] is used since
1. it can solve both linear and non-linear problems
2. it is proven to be a universal approximator that can model all types of function y=f(x)
