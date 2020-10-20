
# Humans vs AI —an  experiment on classical music recognition (in 2 steps)

Using bayesian statistics to find out the relative performance of meat-based organisms against robots

![](https://cdn-images-1.medium.com/max/2000/1*lmsrBo0VIH0OmB0uyrd1yQ.png)

Hey there! In this article we will go through a little experiment that has been done recently (August 2020).

The question we address is the good-old all-terrain:
> “How is the classification-accuracy of humans compared to the one of AI-based methods?”

The question is concise and vague; a useless line in this article if we don’t go into the specifics. That is the purpose of the following two sections.

but before we start:

[**DISCLAIMER:** Full code is public](https://github.com/GastonMazzei/music-ai-experiment). That means you can 1.generate a quiz for humans to answer, 2.collect the results and 3.process them against an AI-based classifier **in only one click**. Ok, actually in like five clicks…

Let’s cut to the chase, shall we?

## 1. Building an experiment for humans: a quiz

***Quick Question: **Can you identify the composer from this sample? options below*

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/WO7NW4nHMkI" frameborder="0" allowfullscreen></iframe></center>

![Options are Vivaldi, Haendel, Bach, Liszt, Stravinsky, Scarlatti, Sor & Haydn](https://cdn-images-1.medium.com/max/3104/1*9xl3ag5wz_yT2fi3tOub1Q.png)*Options are Vivaldi, Haendel, Bach, Liszt, Stravinsky, Scarlatti, Sor & Haydn*

In order to find out how good humans actually are at recognizing authors from short (7 seconds) music samples, a quiz was made. Average-opinion got to be that it isn’t easy!
> # Average attention span is short

![A view of the Google Form’s first page](https://cdn-images-1.medium.com/max/2000/1*nTTSJ3eODnAUZaiUbhx48Q.png)*A view of the Google Form’s first page*

The main thing to point out is that **the quiz was a [randomly-changing Google Form,](http://shorturl.at/irzIS) **i.e. a Google Form in which sound-samples vary with time.

Randomly changing questions allowed us to gather answers for +120 samples while **individual visitors answered only 6**.

This and the fact that **sound samples last 7 seconds **are** **ways to make it more appealing **in the context of dealing with a short attention span**.

*Randomly-changing Google-Form-Quizzes can be made using the public [code of the experiment](https://github.com/GastonMazzei/music-ai-experiment), or using [this](https://github.com/GastonMazzei/random-google-form) brief specific repository. **The form is wired to a spreadsheet so it ultimately comes down to waiting for people to answer and downloading a .csv!** [Quiz-results are also public](https://docs.google.com/spreadsheets/d/1JOVwSh6GSXB4COM1ZyaRAElkiiyusb5v2IWcfWVD1sw/edit?usp=sharing). A discussion about this forms and a tutorial is available in my series:*
[**Dynamical Google Forms: targeting the lazy audience (1 of 2)**
*Taking your polls to the next level by not missing what the laziest (and arguably the busiest) part of your audience…](https://medium.com/@gastonmazzei95/dynamical-google-forms-targeting-the-lazy-audience-1-of-2-ce0279d4a68c)*
[**Dynamical Google Forms: targeting the lazy audience (2 of 2)**
*Taking your surveys to the next level by not missing what the laziest (and arguably the busiest) part of your audience…*medium.com](https://medium.com/@gastonmazzei95/dynamical-google-forms-targeting-the-lazy-audience-2-of-2-682352a61e3c)

## …So …100 respondents later …

**Answers were retrieved as csv and processed using Python’s Pandas.**

*Will it ever cease to amaze me that [for centuries](https://www.biblegateway.com/passage/?search=Luke%202:2) people processed data manually? ***Wrapping up: **a quick glance at the answers

![Table showing correct values for questions and respondents’ answers ([code for csv-to-tables](https://gist.github.com/GastonMazzei/24703003003c66f55c64c1776be119d0) in python).](https://cdn-images-1.medium.com/max/3384/1*h9emGgstGI9HPmihHep8Ww.png)*Table showing correct values for questions and respondents’ answers ([code for csv-to-tables](https://gist.github.com/GastonMazzei/24703003003c66f55c64c1776be119d0) in python).*

![Answer-counts per question for each composer. No conclusions yet, just informative…](https://cdn-images-1.medium.com/max/5492/1*kta4QrrKzO3bwijSUxYyxA.png)*Answer-counts per question for each composer. No conclusions yet, just informative…*

## 2. Building AI-based classification models and comparing them with humans

### AI-classifiers were Feed Forward Neural Networks and Random Forest; **below is a summary of what they are for outcomers**
> *In an attempt to keep the article short, let us briefly define:*
> **A feed-forward multi-class neural network is a probability distribution composed with a smooth nonlinear mapping**. *(1)* At first the smooth mapping transforms our data, and *(2)* at last classification is done using a probability distribution *(image below; parameters are obtained via minimization with gradient descent). ***On the other hand, random forest classifiers are an ensemble of decision trees.**
> The training was done using ~50 songs per composer: by splitting midi works into 7-second-fragments a training set of ~20k points was built. Each point had 500 features representing 7 seconds of music; features included: pitch, duration & volume.

![``Softmax’’: the output probability density of multi-class feed-forward neural-networks](https://cdn-images-1.medium.com/max/2000/1*ycXb0igJB1Db9C3K_VY8Lg.png)*``Softmax’’: the output probability density of multi-class feed-forward neural-networks*

### Finally — specifics of how they will be compared

![The four models that will be compared; the null hypothesis is an 8-sided dice](https://cdn-images-1.medium.com/max/3064/1*elv3gLESh-RBnd91bTi1dA.png)*The four models that will be compared; the null hypothesis is an 8-sided dice*

* In the complex world of multi-class-prediction metrics, we hereby arbitrarily commit to quantifying the models using the “Recall” (i.e. predicted positives over total positives) for each composer.

![Recall as efficiently defined in Wikipedia](https://cdn-images-1.medium.com/max/2176/1*741MBzfpQaDxjFnixLBcCQ.png)*Recall as efficiently defined in Wikipedia*

* **Under Bayesian statistics, modelling the recall as the parameter of a Bernoulli distribution** with ‘recognized/not-recognized’ as sample space and assuming a uniformly-distributed prior **yields that the probability density function for the recall itself is a beta distribution** of parameters ‘α: total predicted true positives’ and ‘β: total sample positives’.

## FINAL RESULTS
> *The domain-value where each density-function peaks is an estimation for the detection rate.*

![Probability density function for the Recall separated by composer. Bottom-right: each color represents a different model (blue — humans) (orange — neural network) (light blue — random classifier or null hypothesis) (red — random forest)](https://cdn-images-1.medium.com/max/6400/1*McDtK3WHcQhri05RO2fUEg.png)*Probability density function for the Recall separated by composer. Bottom-right: each color represents a different model (blue — humans) (orange — neural network) (light blue — random classifier or null hypothesis) (red — random forest)*
> # *IF YOU LIKED IT, FOLLOW ME ON [MEDIUM](https://medium.com/@gastonmazzei95) AND/or [GITHUB](https://github.com/GastonMazzei)!*

![Hope you liked it!](https://cdn-images-1.medium.com/max/8000/0*66zmKnLcj9Ru0sqr)*Hope you liked it!*

**CONCLUSIONS**

* **AI-based classification-models consistently beat humans for every composer** *(except for Stravinsky, for whom not enough training-data was available)*.

* **Humans outperformed the random hypothesis** for over half of the composers. At best, for Vivaldi, they doubled it.

* **The** (perhaps not so fashion?) **random-forest classifier outperformed systematically the neural network**. This is no coincidence: with ~20k datapoints and ~500 features the classification problem is arguably better suited for the former given that the ‘data/degrees of freedom’ ratio allows for more inner-complexity.
