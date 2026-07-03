---
tags:
  - AI
  - Programming
  - Math
---

### Prefix 

For the sake of ease of comprehension, as well as following the status quo, all information surrounding how the network learns, the number of [Neurons](Neuron) etc. are all about a [[Neural Network]] that takes a 28x28 grid of pixels, and identifies what number is shown.

---
### How the network learns

What makes machine learning different from other computer science is that you don’t explicitly write instructions for doing a particular task. In this case, you never actually write an algorithm for recognizing digits. Instead, you write an algorithm that can take in a bunch of example images of handwritten digits along with labels for what they are and adjust those 13,002 weights and biases of the network to make it perform better on those examples.

The labeled images we feed in are collectively known as the "training data".

![[Pasted image 20250428023714.png]]

Hopefully, the layered structure will mean that what it learns generalizes to images beyond the training data. To test this, after training the network, we can show it more labeled data that it’s never seen before and see how accurately it classifies them.

![[Pasted image 20250428024028.png]]

This process requires a lot of data. For recognizing images of digits, the people behind the MNIST database have put together a collection of tens of thousands of handwritten digit images, each labeled with the number they are supposed to represent, that we can use for free.

Saying that the Neural Network is "learning" can be deceptive. Once you see how it works, it feels less like sci-fi magic and a lot more like a calculus exercise. It really just comes down to finding the minimum of a specific function. See [[The Cost Function]].