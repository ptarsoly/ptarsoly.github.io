---
layout: post
title: Contrastive Learning based Hybrid Networks
---

## Paper Information

**Title:** Contrastive Learning based Hybrid Networks for Long-Tailed Image Classification

**Authors:** Peng Wang, Kai Han, Xiu-Shen Wei, Lei Zhang, and Lei Wang

**Conference:** Computer Vision and Pattern Recognition 2021

**Pages:** 943-952

**Year:** 2021

**Link:** [https://arxiv.org/pdf/2103.14267.pdf](https://arxiv.org/pdf/2103.14267.pdf)

## Paper Summary

*Contrastive Learning based Hybrid Networks for Long-Tailed Image Classification* describes an approach to classification that seeks to increase the performance of classifying samples from long-tailed, underrepresented classes. Through a combination of model architecture and loss modifications, the authors show improved performance over other state of the art techniques when faced with class-imbalanced problems.

Before introducing their approach, they perform a review of previous work within long-tailed classification. On the data side, they discuss techniques that synthetically alleviate class imbalances, such as copying old or generating new samples in underrepresented classes. They then introduce modifications to the loss function, where samples from underrepresented classes are weighted to effectively increase their representation. They also discuss methods separating feature learning from classifier learning, which incorporate some of the aforementioned techniques. Finally, they introduce the concept and prior work surrounding contrastive learning, which modifies the loss function with inspiration from unsupervised learning.

They introduce their approach as a framework that is a neural network model with two branches: one to learn features (or representation), and another to learn a classifier. During training, the feature learning branch is given samples with no modifications to sampling, whereas the classifier branch uses class-balanced sampling. Though this implies the branches receive different samples per training iteration, they share their hidden, or "backbone", network layers. Additionally, the two use different loss functions; while the classifier branch uses standard cross entropy, the feature branch uses supervised contrastive loss (SCL). SCL is minimized by both maximizing the similarity of the output with those of the same class, while minimizing the similarity with the output of other classes. Since this implies the need to compute the similarities for every sample, thereby drastically increasing the computational complexity, the authors introduce the use of one prototype output per class, and redefining the loss as prototypical supervised contrastive (PSC) loss. Finally, the importance of each branch within the overall loss function changes during training by multiplying the branch losses with an iteration-varying coefficient. Training starts off with no classifier loss, and gradually transitions to no feature loss instead by the end. During inference, only the classifier branch is used to determine model output.

After explaining the approach, the authors compare its performance to various other state of the art techniques on popular image datasets. In most cases, their SCL-based model performed the best, with PSC typically following as the second best. To prove the combination of parts within the approach brought the increase in classification performance, they performed a number of ablation studies. From using differing sampling strategies, to different loss functions per part, to how they vary the loss during training, the authors show how their two branch SCL and PSC-based approaches outperform other configurations.