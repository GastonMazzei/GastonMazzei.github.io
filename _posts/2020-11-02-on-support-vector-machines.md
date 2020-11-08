---
layout: post
title:  "Mazzei's Blog"
paragraph_title: "On Support Vector Machines"
date:   2020-11-02 11:37:00 -0300
categories: jekyll update
---

<h1><p style='text-align:center'> <b>SUPPORT VECTOR MACHINES USED FOR CLASSIFICATION</b></p></h1>

<b>FORMULATION</b>

There is an hypothesis that is linear on the parameters (*w*)


$$y=\sum w^j \phi_j(\textbf{x}) + b$$

And the optimization implies minimizing a quadratic function with linear constraints, i.e.:

$$argmin_{w,b}||\textbf{w}||^2$$ 

under this linear constraint 

$$t_n(w^T\phi(x_n)+b)\geq 1$$

A variational formulation implies the following 'Lagrangian':

$$L=\frac{1}{2}||w||^2 - \sum _n ^N a_n  { t_n (w^T\phi(w_n) + b)  }$$ 

Thus finally we obtain the error function:

$$E=\sum_{i=0}^NE_p (y(x_i)t_i - 1) + \lambda ||w||^2$$

<b>EXTRA:</b>

A deeper understanding of the optimization problem can be attained by the reader using with the following figure (from <a href="https://www.amazon.com/Pattern-Recognition-Learning-Information-Statistics/dp/0387310738">Bishop</a>):


{% include image.html url="/assets/svm-1.png" description="$$argmax_{\mathbf{w},\mathbf{b}}\left ( \frac{1}{||w||}min_{\mathbf{n}}[ t_n (w^T\phi(x_n)+b) ]\right )$$" w=500 h=500 %}

<b>IF DATA IS LINEARLY SEPARABLE</b>

Where the most 'hardest' penalization that can be applied is the 'infinity penalization' parametrized by:

$$E_\infty = \begin{cases}
 & 0\text{ if } x\geq 0 \\ 
 & \infty \text{ if } x<0 
\end{cases}$$

<b>IF DATA IS NOT LINEARLY SEPARABLE</b>

A 'smoother' error function is defined as follows:

$$\xi _i = \begin{cases}
 & 0\text{ if correctly classified}\\ 
 & |t_i-y(x_i)| \text{ otherwise }
\end{cases}$$

At last the minimization problem can be stated in terms of only one parameter: the relative weight of both terms. i.e.

$$C\sum_i^N \xi_i + \frac{1}{2}||w||^2$$


<b>THE DUAL REPRESENTATION OF THE LAGRANGIAN FORMULATION AND THE INTRODUCTION OF KERNELS</b>

$$L(w,b,a)=\frac{1}{2}||w||^2 - \sum_{n=1}^N a_n [t_n(s^T\phi(x_n)+b)-1]$$

$$\hat{L(a)}=\sum_{n=1}^Na_n-\frac{1}{2}\sum_{n=1}^N\sum_{m=1}^Na_na_mt_nt_mk(x_n,x_m)$$

Where we define the kernel as

$$k(x_n,x_m)=\phi(x)^T\phi(x')$$

And we have parametrized the predictions as: 

$$y(x)=\sum_{n=1}^Na_nt_nk(x,x_n)+b$$

Finally note that the so-called 'Support Vectors' correspond to the condition 

$$t_ny(x_n)=1$$

<b>COMMON KERNELS</b>

$$k(x,x')=X^TX'$$

$$k(x,x')=(X^TX')^2$$

$$k(x,x')=exp(-||X-X'||^2/2\sigma^2)$$


