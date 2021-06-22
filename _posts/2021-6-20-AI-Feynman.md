---
layout: post
title: AI Feynman
---

## Paper Information

**Title:** AI Feynman: a Physics-Inspired Method for Symbolic Regression

**Authors:** Silviu-Marian Udrescu and Max Tegmark

**Journal:** Science Advances, Vol. 6, no. 16

**Pages:** 16

**Year:** 2020

**Link:** [https://advances.sciencemag.org/content/6/16/eaay2631](https://advances.sciencemag.org/content/6/16/eaay2631)

## Paper Summary

*AI Feynman: a Physics-Inspired Method for Symbolic Regression* presents a deterministic algorithm that discovers scientific symbolic models from a given set of associated inputs and outputs known as mysteries. In short, through a divide-and-conquer technique, the algorithm "solves" the mysteries by breaking it down into smaller parts which are computationally tractable to realize into symbolic forms. The authors further compare the algorithm to a previously-created program, Eureqa, and discuss further improvements to their algorithm.

The first part of the algorithm redefines the given mystery by effectively removing all fundamental units from the input and output variables. This operation effectively creates independent variables, simplifying the overall process for future steps.

Once dimensional analysis is complete, a polynomial fit is attempted on the new mystery. Considering dimensional analysis often leads to variables being raised to an integer exponent, this technique proved useful for rediscovering a number of physical relations during experiments.

If a polynomial fit is not found between the variables, a brute-force method is used to test out as many relations between the variables, represented as a string of symbols, before a predetermined stop time, or one of the relations crosses an error threshold.

When neither the polynomial fit or brute force methods work, a separate process to simplify the mystery and separate the variables is employed. To achieve this, the algorithm employs a neural network that can approximate a continuous function, from the discrete set of points making up the mystery, representing the relations between input and output variables. Once the neural network is fit, three tests are employed to simplify the mystery: translational symmetry, separability, and equality of variables. Symmetry and variable equality are desired to decrease the number of variables. Separability allows the mystery to be split into a number of sub-mysteries, joined together by multiplication or addition.

Finally, in the event that none of the aforementioned steps prove to solve the mystery, the input data is transformed by a number of mathematical functions, and these mystery variants repeat these steps over again. For example, in the event of a relation where the output is equal to a constant divided by a polynomial, the transformation step may invert the mystery to then perform a polynomial fit on the denominator.

After presenting the algorithm, the authors compare it to the Eureqa program, which is a genetic algorithm-based algorithm, commonly used for symbolic regression. Of the original 100 mysteries derived from various physics equations outlined in the *Feynman Lectures on Physics*, which were used to develop the AI Feynman algorithm, Eureqa only solved 71 of them, with AI Feynman solving all within the 2 hour window. To compare how they generalize, both were presented an additional 20 mysteries not used in the development of AI Feynman. Still, AI Feynman prevailed, solving 18, whereas Eureqa only solved 3 in the same two hour time window.

Finally, in order to improve AI Feynman, the authors introduce a number of methods. They suggest a method to detect calculus operators in order to treat the mysteries, including those typically modeled as partial differential equations, differently. Further, they elaborate on the need for a different neural network architecture to better handle noise. Additionally, they present different combinations of the brute force step with the function tests in order to either further break the problem down, or reduce the brute force search space. Finally, they claim that using a genetic algorithm on top of a neural network could replace the aforementioned brute force step.
