---
layout: post
title: Learning Equations for Extrapolation and Control
---

## Paper Information

**Title:** Learning Equations for Extrapolation and Control

**Authors:** Subham S. Sahoo, Christoph H. Lampert, and Georg Martius

**Conference:** The 35th International Conference on Machine Learning

**Pages:** 4439-4447

**Year:** 2018

**Link:** [http://proceedings.mlr.press/v80/sahoo18a/sahoo18a.pdf](http://proceedings.mlr.press/v80/sahoo18a/sahoo18a.pdf)

## Paper Summary

*Learning Equations for Extrapolation and Control* presents a technique to extract meaningful symbolic models from a neural network. The authors achieve this through a number of modifications to a typical network including architecture, training, and hyperparameter choices. They then evaluate the technique against previous ones using a number of scenarios, including both modeling and controlling physical systems.

The first modification they propose is a change to the activation functions within the hidden and output layers. Within the hidden layers, every unit's activation function is either a unique unary mathematical operator, such as sine, cosine, and an "identity" operator of the dot product pre-activation, or a multiplicative operator that multiplies two input values together. Within the output layer, special division operators are introduced that ensure the denominators are never negative or approach zero. 

The second modification regards the training process. In order to account for the division by zero problem, penalty terms are introduced into the loss function to avoid the problem on data both inside and outside of the observed range during training. Additionally, in order to realize meaningful coefficients as weights between hidden unit layers, a three-step, phased regularization scheme is utilized to remove meaningless coefficients.

The third change, tuning hyperparameters, selects the number of layers needed for the model's optimal performance. Instead of solely basing performance on error, they define it by model error on the test set, simplicity as a function of sparsity amongst the weights, and optionally error on data out of range of that seen within the test set.

After describing the modifications, the authors present a comparison of the new technique to previous ones. They present a number of techniques for comparison, including a multilayer perceptron network, the symbolic regression program known as Eureqa, and a previous iteration of the new technique but without a division operator. They first evaluate the techniques on learning formulas both with and without division, along with randomly generated formulas. On all three, the new technique performs consistently well, and is the best except for one formula. Similarly, when given problems representing physical systems, the new technique performed with the least error, which further always decreased upon using the out of range data.
