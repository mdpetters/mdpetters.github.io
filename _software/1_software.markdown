---
layout: page
title: Tikhonov
description: A Julia package to perform Tikhonov regularization for small to moderate size problems.
img: /assets/img/tikhonov1.png
importance: 1
---

#### Nature is Cruel

Sometimes the laws of nature conspire to conceal your measurement among other signals that 
are not valuable to you. For example, you are searching for a needle in a haystack. 
Your instrument detects (a) hay, and (b) needles. You need to deconvolve your noisy measurement to
pinpoint that needle. This software solves generic deconvolution problems where overlapping 
signals from various predictable phenomena make your measurement hard to interpret.

Such inverse problems frequently arise in science and engineering applications. Regularization is
 a statistical technique to filter the error in the inversion process. Our 
group uses regularization techniques to post-process data collected in laboratory
and field experiments.


#### Package Description
RegularizationTools.jl bundles a set routines to compute the regularized Tikhonov inverse 
using standard linear algebra techniques. The package features a user friendly interface
and extensive documentation. Check out <a href ="https://mdpetters.github.io/RegularizationTools.jl/stable/" target="_blank" rel="noopener noreferrer">  the documentation </a> and the <a href ="https://github.com/mdpetters/RegularizationTools.jl" target="_blank" rel="noopener noreferrer"> source code</a>. A brief introduction is below.


#### Example
Discrete ill-posed problems are characterized by systems of equations where the inverse 
solution is highly-sensitive to noise superimposed on the data. The problems are common in 
science and engineering, including in the Atmospheric Sciences. Consider the following system of
linear system of equations

$${\bf {\rm {\bf A}{\rm x}={\rm y}}}$$

where $${\bf {\rm {\bf A}}}$$ is a square design matrix, $${\rm x}$$ is a vector of input 
parameters and $${\rm y}$$ is a vector of responses. To estimate unknown inputs from 
response, the matrix inverse can be used

$${\rm x={\rm {\bf A}}^{-1}y}$$

However, if a random measurement error $$\epsilon$$ is superimposed
on $${\rm y}$$, i.e. $$b_{i}=y_{i}+\epsilon_{i}$$, the estimate $${\rm \hat{x}}$$ from the matrix inverse 

$$ {\rm \hat{x}={\rm {\bf A}}^{-1}b}$$ 

becomes dominated by contributions from data error for large systems. Consider the following example system of 100 equations. The vector $$\rm{x}$$ of input variables has 100 elements. The code fragment computing the solution using the pseudo-inverse of $$\rm{y}$$ (no errors) and $$\rm{b}$$ (with errors superimposed)  

{% highlight julia %}
y = A * x
b = y + 0.1y .* randn(100)
x = pinv(A) * y
x̂ = pinv(A) * b
{% endhighlight %}

<img src="/assets/img/regularization.png" alt="drawing" width="700"/>

The figure in the middle shows the correct soltion for x. The figure to the right shows
that the random error superimposed on $$\rm{b}$$ makes the inversion unusable.



#### Regularization

Regularization is a means to filter this noise by solving the minimization problem 

$$
{\rm {\rm x_{\lambda}}}=\arg\min\left\{ \left\lVert {\bf {\rm {\bf A}{\rm x}-{\rm b}}}\right\rVert _{2}^{2}+\lambda^{2}\left\lVert {\rm {\bf L}({\rm x}-{\rm x_{0}})}\right\rVert _{2}^{2}\right\} 
$$

where $${\rm x_{\lambda}}$$ is the regularized estimate of $${\rm x}$$,
$$\left\lVert \cdot\right\rVert _{2}$$ is the Euclidean norm, $${\rm {\bf L}}$$ is the 
Tikhonov filter matrix, $$\lambda$$ is the regularization parameter, and $${\rm x_{0}}$$ 
is a vector of an *a priori* guess of the solution. The initial guess can be taken to be 
$${\rm x_{0}}=0$$ if no *a priori* information is known. The matrix $${\rm {\bf A}}$$
does not need to be square. 

For $$\lambda=0$$ the regularization problem reverts to the ordinary least
squares solution. If $${\rm {\bf A}}$$ is square and $$\lambda=0$$,
the ordinary least-squares solution is $${\rm \hat{x}={\rm {\bf A}}^{-1}b}$$. For large $$\lambda$$ 
the solution reverts to the initial guess., i.e. 
$$\lim_{\lambda\rightarrow\infty}{\rm x_{\lambda}}={\rm x_{0}}$$.

#### RegularizationTools.jl
RegularizationTools.jl is a set of tools to help solve the regularization problem. It contains
fast algorithms to solve for $$\mathrm{x}_\lambda$$, a simple and flexible interface, and 
an algorithm to compute the design matrix from a forward model. It is free software. Learn more
in  <a href ="https://mdpetters.github.io/RegularizationTools.jl/stable/" target="_blank" rel="noopener noreferrer"> on the project's website </a>.



