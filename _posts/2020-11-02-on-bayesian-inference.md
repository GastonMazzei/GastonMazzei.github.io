---
layout: post
title:  "Mazzei's Blog"
paragraph_title: "On Bayesian Inference"
date:   2020-11-02 16:02:00 -0300
categories: jekyll update
---

<p style='text-align:center'><b>BAYES THEOREM</b>
$$p(A|B)=P(B|A)\frac{P(A)}{P(B)}$$
</p>

{% include image.html url="/assets/bayes.jpeg" description="Thomas Bayes" w=200 h=200 %}
<br><br>
<p style='text-align:center'><b>A THEORETICAL BACKGROUND FOR A COMMON CLAIM</b>
<br>
<i>"the probability of X is p"</i>
</p>
<br>

The posterior distribution is the distribution of the model's parameters after taking into account the observed data. The bottom line is that with enough data the posterior will peak at some value and that is the most certain unique value that can be assigned to the parameters. Naturally, with the parameters of the model we can calculate the desired magnitude (e.g. the mean or the standard deviation of false positives). One common operation is to assume the prior information about the parameter as uniformly distributed and end up maximizing the model's likelihood, i.e. "MODEL" in the following figure.
<br>
<br>

{% include image.html url="/assets/bayesian-system.png" description="" w=450 h=200 %}

<br>
<br>

The mathematical formulation of bayesian inference. 'Finding the parameter where the posterior peaks' allows refering to the probability as a single number (1) The model that explains the data; e.g. a Poisson process (2) The hypothesis of a parametrization for the parameters before any data is taken into account (3) A constant number for probability calibration (4) The posterior distribution
<br><br>
<br>

<p style='text-align:center'><b>Interesting papers</b></p>

<br>
1) A paper that treats model selection. Addresses the self-arising Occam's Razor's properties of bayesian systems and it's connection with differential geometry and statistical mechanics: 
<a href="https://arxiv.org/abs/cond-mat/9601030"> "Statistical Inference, Occam's Razor and Statistical Mechanics on The Space of Probability Distributions"</a> <i>Vijay Balasubramanian; Princeton</i>

<br>
2) A paper that insists on very specific analogies between thermodynamics and bayesian inference, while providing very interesting differential geometry insights.
<a href="https://arxiv.org/abs/1706.01428"> "On the correspondence between thermodynamics and inference" </a> <i>Colin H. LaMont, Paul A. Wiggins; University of Washington</i>

<br>
3) Arguments against using bayesian inference in high dimensionality models
<a href="http://yann.lecun.com/exdb/publis/pdf/lecun-06.pdf"> PDF by Yann Le Cunn</a>


<p style='text-align:center'><b></b></p>

<p style='text-align:center'><b></b></p>

