---
layout: post
title: Maximum Likelihood Procedures
date: 2023-02-16 11:12:00-0400
description: multivariate-analysis
tags: LinearAlgebra DataScience
categories: 
---

## Maximum Likelihood and Multivariate Normal Distribution

### Model, Parameter, Objective Function, and Optimization
Any procedure is underlain by a model that can be expressed as

$$
\tag{1}
Data \cong \phi(\Theta)+Errors
$$

where $\Theta$ denotes the parameters to be estimated. For instance, in KMC cluster analysis $\Theta$ is {\(\mathbb{G, C}\)}. In regression analysis, the \(\Theta=[\vec{b},c]\) and $\phi(\vec{b},c)=\mathbb{X}\vec{b}+c\vec{1}$. 

An analysis procedure modeled as (1) estimates parameter *\(\Theta\)* values. This is formulated as “Obtaining \(\Theta\) that optimizes an objective function *obj(\(\Theta\))* subject to a constraint on \(\Theta\)”. 

Here, the term "optimizes" refers to either "minimizes" or "maximizes", and some function can be used as *obj(\(\Theta\))*. In *least squares method*, the least squares are used as *obj(\(\Theta\))*, which are generally expressed as \(||Data-\phi(\Theta)||^2\), with "optimizes" referring to "minimizes" and \(\Theta=[\vec{b},c]\) is not constrained.

### Maximum Likelihood Method
A maximum likelihood (ML) method can be formulated by rephrasing“optimizing” and “an objective function” as "maximizing" and "probability", respectively. To note, ML uses notion of probabilities, which is not used in the LS method. 

An simple example illustrating ML: suppose a black box contains black and white balls, where the total number of balls is known to be 100, but the number of black or white balls is unknown. We use \(\theta\) for the number of black ones. In order to estimate \(\theta\), a ball was drawn from the box and returned back to the box five times, which produces the following data set

$$
\vec{d}=[1,0,,1,0]^T
$$

Here, \(d_i=1, d_i=0\) indicate black and white balls drawn, respectively, with \(d_i\) denotes the ith element of \(\vec{d}\).

The probability of \(d_i = 1\) observed (i.e., a black ball chosen) and that of \(d_i = 0\) are expressed as

$$
P(d_i=1|\theta)=\frac{\theta}{100} \\
P(d_i=0|\theta)=1-\frac{\theta}{100} 
$$

Further, we suppose the balls were chosen mutually independently. Then, the
probability of the data set \(\vec{d}\) is

$$
P(\vec{d}|\theta)=(\frac{\theta}{100})^2(1-\frac{\theta}{100})^3
$$

For estimation of the value of \(\theta\), the ML method can be used. The idea of the method can be stated as “Obtaining the parameter value such that the occurrence of an event is the most likely”. Here, the “event” refers to the observation of a data set, i.e., observing \(\vec{d}\) and “how likely it is that the event will occur” is measured by its *probability*. 