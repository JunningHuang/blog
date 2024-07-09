---
title: Recall Basic Probability
draft: false
tags:
  - Probability
---
## Overview
This note recall some basic stuffs of probability, include:
- Basic concepts of joint distribution and conditional distribution
- The propagation of uncertainty

## Joint and Conditional Distribution
Consider the continuous single variable case, to describe the uncertain behavior, the concept of random variable is introduced, and CDF, a single variable function, is used to describe the probability of certain event happens between an interval. Then PDF is used to describe the density of the CDF, so that we could use calculus to form the whole theory of probability.

Move on to the multi-variable case, because more than one random event happens, we use joint distribution to describe it, namely a multi-variate function, e.g. instead of a density function with only one input $p(x)$, now we have $p(x,y)$ a density function with two inputs. The events themselves could affect each other or completely independent from each other. That's why we introduce the idea of covariance, from $E[(x-E[x])(x-E[x])^T]$ to $E[(x-E[x])(y-E[y])^T]$. 

Conditional distribution and joint distribution are quite similar, conditional distribution is still a multi-variate function, e.g. $p(x|y)$ is a density function with two inputs, but it would be normalized by a factor $p(y)$. But it's nice to think it as a function of $x$ with some fixed $y$, that would show the intrinsic motivation of conditional probability, we would use this perspective to derive the conditional distribution of the Gaussian distribution.

## The Propagation of Uncertainty
We have a random variable $X$ and $Y$, and we have $y=ax$. In the lens of probability, if we know $X\sim\mathcal{N}(\mu,\sigma^2)$, how to calculate the probability of $Y$. Let's substitute $x=y/a$ into the PDF of $X$. 
$$
\begin{aligned}
p(Y/a=y/a)=C\exp(-(y/a-\mu_x)^2/\sigma_x^2)
\end{aligned}
$$
here $C$ is the constant term, then rearrange it we have
$$
\begin{aligned}
p(Y/a=y/a)=C\exp(-(y-\mu_y)^2/\sigma_y^2)
\end{aligned}
$$
where $\mu_y=a\mu_x$, $\sigma_y^2=a^2\sigma_x^2$. Extend to the multivariable case, $y=Ax$, assume $A$ to be invertible
$$
\begin{aligned}
p(A^{-1}Y=A^{-1}y)=C\exp(-(A^{-1}y-\mu_x)^T\Sigma_x^{-1}(A^{-1}y-\mu_x))
\end{aligned}
$$
rearrange we have,
$$
\begin{aligned}
p(A^{-1}Y=A^{-1}y)=C\exp(-(y-\mu_y)^T\Sigma_y^{-1}(y-\mu_y))
\end{aligned}
$$
where $\mu_y=A\mu_x$ and $\Sigma_y=A\Sigma_xA^T$. It's easy to know that if we shift $y$ to $y=ax+b$, then only the mean value would change but not the covariance, namely the result would be $\mu_y=A\mu_x+b$. 

**Remark**
We derive the result but what does the result tell us? First of all, Gaussian distribution comes from the study of the error of least square approach, mean is the prediction and covariance describe the property of the errors. 

Let's consider only the case $a>0$ or $A$ has only positive eigen values. Let's say I want to measure the thickness of a book, and with the tape the thickness of one book follows the Gaussian distribution. And we want to know about the thickness of 10 books, we can think that our prediction is 10 * the thickness of one book, but the accumulated error would be 10 times bigger. Since covariance is somehow like the square of the error, so it's 100 times bigger. But if we want to estimate half-of a book, the prediction would 0.5 * the thickness of one book, and the error would cut half.