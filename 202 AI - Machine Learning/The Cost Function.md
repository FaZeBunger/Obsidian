### The Cost Function

Remember, our network's behavior is determined by all of its weights and biases. The weights represent the strength of connections between each neuron in one layer and each neuron in the next. And each bias is an indication of whether its neuron tends to be active or inactive. 

![[Pasted image 20250428175520.png]]

To start things off, initialize all the weights and biases to be random numbers. The network will perform horribly on the given training example since it's just doing something random.

For example, if you feed in this image of a 3, the output layer just looks like a mess:

![[Pasted image 20250428180723.png]]

So how do you programmatically identify that the computer is doing a lousy job and then help it improve?

What you do is define a cost function, which is a way of telling the computer, "No, bad computer, that output layer should have activations which are 0 for most neurons, but with a 1 for the third neuron. What you gave me is utter trash!"

![[Pasted image 20250428181925.png]]

To say that a little more mathematically, add up the squares of the differences between each of these trash output activations and the values you want them to have, also known as [[Mean Squared Algorithm|MSA]]. We'll call this the [[Cost]] of a single training example.

![[Pasted image 20250428182630.png]]

The cost is small when the network confidently classifies this image correctly but large when it doesn't know what it's doing. 

We aren't just interested in how the network performs on a *single* image. To really measure its performance, we need to consider the **average** cost over all the tens of thousands of training examples. This average is our measure of how lousy the network is and how bad the computer should feel. See [[The Cost Over Many Examples]]

There are many types of cost functions, to name a few:
- [[Mean Squared Algorithm]] (MSA)
- [[Binary Cross Entropy/Logloss]]
- [[Categorical Cross-Entropy]] 
- [[Kullback-Leibler Divergence]]
- [[Root Mean Squared Error]] (RMSE)
- [[Mean Absolute Error]] (MAE)

Unfortunately, just telling the computer what a terrible job it's doing isn't very helpful. You also want to tell it how it should change the weights and biases so as to improve. This is where [[Minimizing the Cost Function]] comes in.