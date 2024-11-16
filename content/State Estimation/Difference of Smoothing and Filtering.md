---
title: Difference of Smoothing and Filtering
draft: false
tags:
  - Smoothing
  - Filtering
  - state_estimation
---
Take SLAM as an example. We want to know the current state of the system. Smoothing formulate the state estimation as trajectory optimization, or MAP problem. Namely, given states $\mathcal{X}=\{x_1, \cdots, x_{K} \}$, and measurements $\mathcal{Y}=\{y_{1},\cdots,y_{K} \}$, the formulation is 
$$
\begin{aligned}
\text{argmax}_{\mathcal{X}}\ p(\mathcal{X}|\mathcal{Y})
\end{aligned}
$$
Note that smoothing targeting on the whole trajectory. The goal can be decomposed with the Bayesian theorem and then it's basically a nonlinear least square problem.

But for filtering the problem formulation is a bit different, filtering only care about the current state, so the inference problem is
$$
\begin{aligned}
\text{argmax}_{x_{k}}p(x_{k}|\mathcal{Y})
\end{aligned}
$$
So from the difference of formulation one could tell that, since smoothing is optimizing a trajectory-based loss, the estimation of current state is usually more accurate compare with filtering. Unfortunately the computational graph is very huge so techniques need to introduce so accelerate the optimization to run realtime.

On the other hand, filtering is much less computational intensive but it's only a point estimator for the current state, though with a good design of observer, it can converge to the real state globally or almost globally but in theory is not as accurate as smoothing.

Also to clarify a bit the definition of smoothing in the book of "Bayesian filtering and smoothing", they definite smoothing as 
$$
\begin{aligned}
\text{argmax}_{x_{m}}p(x_{m}|\mathcal{Y})
\end{aligned}
$$
where $m<K$. It's different from the definition in SLAM, but if we assume i.i.d., then this formulation exposes a structure of smoothing. In smoothing, the future is used to update the past as well, which is the crucial part of smoothing.