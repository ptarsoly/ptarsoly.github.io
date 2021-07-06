---
layout: post
title: Decoupling Representation and Classifier for Long-Tailed Recognition
---

## Paper Information

**Title:** Decoupling Representation and Classifier for Long-Tailed Recognition

**Authors:** Bingyi Kang, Saining Xie, Marcus Rohrbach, Zhicheng Yan, Albert Gordo, Jiashi Feng, and Yannis Kalantidis

**Conference:** International Conference on Learning Representations

**Pages:** 16

**Year:** 2020

**Link:** [https://arxiv.org/pdf/1910.09217.pdf](https://arxiv.org/pdf/1910.09217.pdf)

## Paper Summary

*Decoupling Representation and Classifier for Long-Tailed Recognition* explores treating neural networks as a combination of two separate entities, a learned data representation and a classifier, in order to increase the accuracy of classifying long-tail distributed, underrepresented classes. Various strategies are employed for both entities, and the end results are compared to both each other and the traditional method of treating both jointly together.

In order to accurately learn representations for the long-tail distributed classes, two types of techniques during training are explored: data sampling and loss re-weighting. For the first, two extremes are presented: each sample has equal probability of selection, known as instance-balanced sampling, and then each class has equal probability of selection, known as class-balanced sampling. In the middle, a third strategy is presented, where the square root of each class sample count is taken and a similar selection strategy to class-balanced sampling is carried out. Additionally, they present another method which continuously changes with the number of training epochs, from instance to class-balanced sampling. The latter technique to learn representations, though not explored as much as the former, reweights the loss function based on both the instance and class levels.

Within a neural network, the output layer is typically considered a classifier. Generally speaking, it need not even be a network layer, as the outputs of the representation can be treated as inputs to any other classifier of choice. To choose a classifier fit for the newly-learned representation, four main options are investigated. First, in a method called Classifier Re-Training (cRT), only the output layer is retrained using class-balanced sampling. Second, Nearest Class Mean (NCM) takes a departure from the output layer approach of a classifier. Instead, the mean vector for the output of the representation for each class is computed. Each test sample is then classified based on the closest class mean vector. Third, the tau-normalized classifier normalizes every weight between the representation output and the classifier by the L2 norm raised to a hyperparameter, tau, of the weights connecting the former layer with the latter on a class-by-class basis. The authors claim that this method corrects imbalanced decision boundaries. Finally, Learnable Weight Scaling (LWS) is similar to the third option, but effectively allows for the learning of the tau hyperparameter.

In order to compare the methods outlined for representation learning and classification, three image datasets with hundreds to thousands of categories, many following a long-tailed distribution, were introduced. For each dataset, at least one network architecture was explored, with each at minimum including a form of hidden and output layers. They first compare the sampling strategies presented for representation learning, revealing that instance-balanced sampling, combined with decoupled strategies for training, performs the best on classes with low representation. Second, they compare the weight norms of the different classifier options, finding that the tau-norm method is the most consistent amongst all classes. Finally, they compare their classifiers to others meant to deal with data imbalances, which shows the cRT, tau-norm, and LWS methods perform better than all previously proposed methods for the given datasets and network architectures.
