---
aliases: 
tags:
  - AI
  - MachineLearning
  - Programming
  - Math
---
### Finding an input

To make it easier, rather than struggling to imagine this cost function with all the inputs, let’s imagine a simple function with one number as an input, and one number as an output.

So how do you find an input that minimizes the cost function?

You'll remember from Calculus that you can sometimes figure out that minimum explicitly by solving for when the slope is zero. However, that's not always feasible for really complicated functions, and it certainly won't be for our function defined in terms of an ungodly number of parameters. 

A more flexible tactic is to start at a random input and figure out which direction to step to make the output lower. Specifically, find the slope of the function where you are. If the slope is negative, shift to the right. If the slope is positive, shift to the left. 

![[Pasted image 20250428190752.png]]

Checking the new slope at each point and doing this repeatedly, you approach some local minimum of the function. 

![[Pasted image 20250428190931.png]]

Notice that even with a simple single variable function, there are still several valleys you can fall into. It depends on what random input you start at, and there's no guarantee that the local minimum you land in will be the smallest possible value for the cost function. 

Also, notice how if you make your step sizes proportional to the slope itself when the slope flattens out towards a minimum, your steps will get smaller and smaller, and that keeps you from overshooting. 

Now, bumping the complexity up a bit, imagine a function with two inputs and one output. You might think of the input space as the xy-plane, with the cost function graphed as a surface above it. 

![[Pasted image 20250428191509.png]]

Instead of asking about the slope of the function, you ask which direction you should step in this input space to decrease the output of the function most quickly. Again, think of a ball rolling down a hill. 

### Using the Gradient

In this higher dimensional space, it doesn't really make sense to talk about the "slope" as a single number. Instead, we need to use a vector to represent the direction of steepest ascent. 

In multivariable calculus, this vector is called the gradient, and it tells you which direction you should step to *increase* the function most quickly.

Naturally enough, taking the negative of that vector gives you the direction to step which *decreases* the function most quickly. What's more, the length of that gradient vector is an indicator for just how steep that steepest slope is. 

So the algorithm for minimizing this function is to compute this gradient direction, take a step downhill, and repeat that over and over. This process is called “gradient descent.”

![[Pasted image 20250428192147.png]]

And remember, the cost of our function is specially designed to measure how bad the network is at classifying the training examples. So changing the weights and biases to decrease the cost will make the network's performance better!

In practice, each step will look like $-\eta \Delta C$ where the constant $\eta$ is known as the learning rate. The larger it is, the bigger your steps, which means you might approach the minimum faster, but there's a risk of overshooting and oscillating a lot around that minimum. 

It's the same basic idea for a function with some $n$ number inputs instead of two inputs.

---
### Another Way to think about the Gradient

Imagine organizing all the weights and biases for the entire network into one big column vector with $n$-number entries. Then the negative gradient of the cost function will also be a vector with $n$-number entries. 

![[Pasted image 20250428193042.png]]

The vector on the left is a list of all the weights and biases for the entire network. The vector on the right is the negative gradient, which is just a list of all the little nudges you should make to the weights and biases (on the left) in order to move downhill.

The negative gradient is a vector direction in this insanely huge input space that tells you what nudges to those $n$-number of numbers would cause the most rapid decrease to the cost function.

