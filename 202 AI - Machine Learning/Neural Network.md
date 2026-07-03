---
aliases:
  - CNN
  - RNN
  - Machine Learning
tags:
  - Programming
  - AI
cssclasses:
---

### Description 

A neural network is a mathematical way of expressing/mimicking a human brain. To put it simply, we can define a neural network as a program where we don't program the output, and instead train the program to take an input and give us the output we desire. A neural network is comprised of [[Neuron|Neurons]]. 

### Types of Neural Networks

There are many variants of neural networks, such as [[Convolutional Neural Networks]] (CNN), [[Recurrent Neural Networks]] (RNN), transformers, and countless others. 

### How it works

A Neural Network is at it's core, just a bunch of [[Neuron|Neurons]] connected together. A [[Neuron]] is the basic building block of a Neural Network. A [[Neuron]] can only store a value 0.0 through 1.0. Because of this, any input we want to put into our Neural Network must first be broken down and turned into a value between 0.0 and 1.0.


### Layers

A Neural Network is broken up into several layers. The first layer is the input layer. The input layer will have as many neurons as inputs you want to give the neural network. After that, are the hidden layers, and then finally the output layer. The output layer will have as many [[Neuron|Neurons]] in it as possible outputs of the Neural Network. 

The hidden layers are any layers in-between the input and output layers. There can be any number of hidden layers in a given Neural Network, and each layer can have an arbitrary number of [[Neuron|Neurons]] inside of it. The numbers of hidden layers and [[Neuron|Neurons]] in a Neural Network can affect the outputs of a Neural Network, and change its accuracy etc.

![[Pasted image 20250428012924.png]]
### Why Use Layers? 

You'll notice in the image above, that every [[Neuron]] is connected to each [[Neuron]] in the next layer. This indicates how the activation of one [[Neuron]] in one layer, the number inside of it, has some influence on the activation of each [[Neuron]] in the next layer. 

Not all connections are equal though. Some will be stronger than others, and determining how strong these connections are is really the heart of how a neural network operates, as an information processing mechanism.

Layers break problems into bite-sized pieces. 

You can imagine [[Neuron|Neurons]] in a Neural Network to correspond to certain attributes. For example:

![[Pasted image 20250428013839.png]]

And then you can imagine that each of those parts, could be broken down into more parts, like this: 

![[Pasted image 20250428013939.png]]

You can think of it as the earlier [[Neuron|Neurons]] correspond to more general or smaller pieces, and then using the combinations of these pieces, we can find larger more complex pieces from it.


### Passing Between Layers

Now that we can visualize what these [[Neuron|Neurons]] may be doing, how do we implement it? What we do is we assign a **weight** to each of the connections between [Neurons](Neuron.md). These weights are just numbers. 

Each weight is an indication of how its neuron in the previous layer corresponds to the neuron in the next layer. 

If a neuron in the first layer is on, then a **positive** weight suggests that the neuron in the second layer should also be on, and a **negative** weight suggests that the neuron in the second layer should be off. 

Of course, these weights will interact and conflict in interesting ways, but the hope is that if we add up all the desires from all the weights, the end result will be a neuron that does a reasonably good job of detecting the edge we’re looking for (as long as the weights are well-chosen).

To actually compute the value of this second-layer [Neuron](Neuron.md), you take all the activations from the neurons in the first layer, and compute their weighted sum.

$w_1a_1 + w_2a_2 + w_3a_3 + ... + w_na_n$

### Sigmoid Squishification

The result of the weighted sum like this can be any number, but for this network we want the activations to be values between 0.0 and 1.0. So it's common to pump this weighted sum into something that squishes the real number line into the range between 0 and 1.

One common function that does this is called the "sigmoid" function, also known as a logistic curve, which we represent using the symbol $\sigma$ . Very negative inputs end up close to 0, while very positive inputs end up close to 1, and it steadily increases around 0. So the activation of the neuron here will basically be a measure of how positive the weighted sum is.

![[Pasted image 20250428020721.png]]

Maybe though, we don't want the neuron to light up when the weighted sum is bigger than 0. Maybe we only want it to be meaningfully active when that sum is bigger than, say, 10. That is, we want some *bias* for it to be inactive.

What we'll do then is add some number, like -10, to the weighted sum before plugging it in to the sigmoid function that squishes everything into the range between 0 and 1. 

We call this number a *bias*. 

![[Pasted image 20250428021142.png]]

So the weights tell you what pixel pattern this neuron in the second layer is picking up on, and the bias tells you how big that weighted sum needs to be before the neuron gets meaningfully active.

This is just the math for a single neuron. For an actual Neural Network, with many neurons, this would get tedious to write and compute.

Instead, we can express an entire layer like this:

![[Pasted image 20250428021917.png]]

Where we use matrix multiplication to get the weighted sum for all neurons, then adding the bias, and then finally using the sigmoid function on it in order to squish the new values.

### The Network is just a Function 

When you think about it, a Neural Network takes in some $n$ number of inputs and spits out a value. Not only that though, each [Neuron](Neuron) in the hidden layers, can be considered a function of all the neurons in the previous layer, and the neurons in that layer all functions of the layer before it, and so on. 

It's an absurdly complicated function, because it takes in some $n$ number of inputs, as well as weights for each connection between each neuron. Leading to exponentially larger networks as we add neurons. It's extremely complicated but, it's a function nonetheless.