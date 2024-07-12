---
title: Bayesian Filtering
draft: false
tags:
  - state_estimation
  - Statistical_Inference
  - Bayesian
---
## Overview
The Bayesian filtering framework cast the filtering problem as a inference problem, the goal is to estimate the posterior distribution of the current state given a history of measurements/observations. 
## Problem Statement
Given a dynamics model and a measurement model, usually they're linear:
$$
\begin{aligned}
\text{Probabilisitc Dynamics Model: }\ &p(x_k|x_{k-1},u_{k-1})\ \text{or}\ p(x_k|x_{k-1})\\
\text{Probabilisitc Measurement Model: }\ &p(y_k|x_k)
\end{aligned}
$$
With the prior distribution $p(x_{k-1}|y_{1:k-1})$ estimated from before and the current measurement $y_k$, we would like to estimate the posterior distribution $p(x_k|y_{1:k})$. 
## Bayesian Filtering
There are two steps for Bayesian filtering, prediction and update. Let's first consider only the state-affine case.
$$
\begin{aligned}
\text{Prediction: }\ p(x_k^-|y_{1:k-1})&=\int p(x_{k}^-|x_{k-1})p(x_{k-1}|y_{1:k-1})dx_{k-1}\\
\text{Update: }\ p(x_k|y_{1:k})&=p(y_k|x_{k}^-)p(x_k^-|y_{1:k-1})/Z
\end{aligned}
$$
where $Z$ is the partition function which satisfies $Z=\int p(y_k|x_k^-)p(x_k^-|y_{1:k-1})dx_k^-$. 

Consider a more probabilistic perspective for Bayesian filtering
- The prediction step is computing the marginal distribution as a prediction for current state, using the prior estimation $p(x_{k-1}|y_{1:k-1})$ and likelihood, which is the probabilistic dynamics model $p(x_k^-|x_{k-1},y_{1:k-1})$. 
- The update step is to compute the posterior distribution $p(x_k|y_{1:k})$ as an estimation of the current state using the current measurement, using the predictive distribution $p(x_k^-|y_{1:k-1})$ as prior and the measurement model $p(x_k|y_{1:k})$ as the likelihood function.

**Remark**
Back from the conditioning of probability, in this case
$$
\begin{aligned}
p(x_k|y_{1:k})=p(x_k,y_k|y_{1:k-1})/p(y_k|y_{1:k-1})
\end{aligned}
$$
it's easy to verify this equality, just write down the definition of $p(x_k|y_{1:k})$ and divided with $p(y_{1:k-1})$ , but how to have an intuition for it? One can think that the division, or more precisely, normalization is try to remove the uncertainty of $p(y_k|y_{1:k-1})$, which means $y_{1:k}$ is known.
## Personal Remark
It's very beautiful and consistent to treat filtering as an inference problem, the idea is very neat. But how to analyze the convergence of the filtering algorithm and is it possible to figure out why my filtering algorithm doesn't work under such framework is questionable.