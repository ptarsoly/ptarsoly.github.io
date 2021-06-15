---
layout: post
title: Discovering Symbolic Models
---

## Paper Information

**Title:** Discovering Symbolic Models from Deep Learning with Inductive Biases

**Authors:** Miles Cranmer, Alvaro Sanchez-Gonzalez, Peter Battaglia, Rui Xu, Kyle Cranmer, David Spergel, and Shirley Ho

**Conference:** Advances in Neural Information Processing Systems (NeurIPS) 33

**Pages:** 9

**Year:** 2020

**Link:** [https://arxiv.org/pdf/2006.11287.pdf](https://arxiv.org/pdf/2006.11287.pdf)

## Paper Summary

*Discovering Symbolic Models from Deep Learning with Inductive Biases* describes the use of neural networks in guiding the creation of algebraic expressions that represent physical models. As motivation for their work, they initially present two ways to model physical relationships: creating algebraic models through symbolic regression and deep learning. After presenting challenges in finding symbolic expressions using each method individually, they present a combination of both, claiming benefits from both techniques.

The type of network used is called a Graph Neural Network (GNN). GNNs are particularly useful for representing relationships between physical objects and their properties. A typical GNN is a collection of multilayer perceptron (MLP) neural networks, some of which are effectively tasked with working on subproblems. First layers typically deal with learning how objects, represented as graph nodes, interact with each other, giving them the name *edge models*. Outputs of the edge models are referred to as messages, which are effectively features created during training. The output layer consists of MLPs tasked with learning how interactions between objects affect individual objects, and take both messages and object properties as input. The authors claim that this network structure creates the inductive bias needed to model the physical world while simplifying the symbolic regression process. In order to further generalize the results of the GNN, the authors experiment with different forms of regularizing the edge model results, including L1, KL, and bottleneck (constrained to problem dimensionality) style methods.

Speaking of symbolic regression, the technique is a genetic programming-based method to create algebraic equations, using variables, constants, and a variety of operators. Similar to many genetic algorithms, a population of equations are created, and each individual is evaluated using a fitness measure that factors in accuracy and simplicity. In order to create symbolic equations relevant to this work, they use the intermediate and final models within the GNN to determine the fitness of each equation. In this case, they assume that the output model from the GNN can be composed of results from intermediate models, including edge models. This assumption drastically reduces their search space, decreasing the amount of effort needed for *fit* results, because they divide up the overall model into smaller chunks.

In order to prove the efficacy of their method, the authors introduce three problems. The first problem investigated modeling the interaction of particles using Newtonian Dynamics. The overall goal was to determine the instantaneous acceleration on the particles, given their relationships (forces and distances from each other) and individual properties (mass and charge). After experimenting with the aforementioned regularization techniques, they found that the bottleneck and L1 methods worked the best in the case of the network and symbolic regression performance.

The second problem delved into modeling the energy of a system using Hamiltonian Dynamics. The object was to not only determine the overall system kinetic energy, but the kinetic energy with respect to each pair of particles. Here, the former was modeled using the overall model, and the latter was modeled using an equivalent edge model. Similar to the first problem, the L1 regularization technique proved to outperform the other methods.

Finally, the third problem presents a method for determining the density of a dark matter halo, given surrounding halo properties. This problem differs from the first two, because currently there are no symbolic models that accurately represent the phenomenon. After ingesting the dataset of halos, and defining how they relate to each other, the GNN was created and symbolic regression was performed, both for instances with and without the mass of a halo. Their results achieve better performance, even without the mass attribute, than previously derived equations. Further, they claim that this problem proves that their method can be used in demystifying uncharted phenomena.