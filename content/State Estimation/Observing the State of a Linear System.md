---
title: Observing the State of a Linear System
draft: false
tags:
  - observer
  - state_estimation
  - linear_system
---
> This note reviews the idea of observer in David Luenberger's seminal paper. It's the first time that the mathematical meaning of an observer is being clarified. David Luenberger only describe the linear system case but the technique that being used in this paper is far beyond linear systems. David published this paper in 1964 and after more than 30 years, the idea is "re-discovered" by Nikolaos Kazantzis, Costas Kravaris for designing nonlinear observer, the so-called KKL observer.

## Overview
The goal of this paper is to design an observer $z=h(y,u)$ for the linear system
$$
\begin{aligned}
\dot{x}&=Ax+Bu \\
y&=Cx
\end{aligned}
$$
David proposes the idea of transforming the original linear system into a new coordinate with the invertible transform $z=Tx$, and design an observer in the new coordinate, and then transform the coordinate back to get an estimation for $x$. Take a linear system without input as an example $\dot{x}=Ax$. The observer in the new coordinate is 
$$
\begin{aligned}
\dot{z}=Gz+Kx
\end{aligned}
$$
Substitute $z=Tx$ and we have 
$$
\begin{aligned}
T \dot{x}&=GTx+Kx\\
T \dot{x}&=TAx
\end{aligned}
$$
Then it's easy to notice that 
$$
\begin{aligned}
TA - GT=K
\end{aligned}
$$
The transformation $T$ exists if the above algebraic equation has solutions. This is well studied problem that if the eigen values of $A$ and $G$ are different, then there exists a solution.

How to guarantee the invertibility of $T$? In this paper, he proposes to use the identity matrix as $T$, aka the state of the observer is the same as the system. If we select $T=I$, then $G=A-K$. If we introduce the output $y=Cx$, then $G=A-KC$, and the observer in the end is
$$
\begin{aligned}
\dot{z}=(A-KC)z+Ky
\end{aligned}
$$
It's easy to note that this is the classic Luenberger observer with the error tracking term $y-Cz$
$$
\dot{z}=Az+K(y-Cz)
$$
## Existence of transform T
The existence of transform depends on the matrix Lyapunov equation.
$$
TA-BT=C
$$
Here $T\in \mathbb{R}^{m \times n}$, $A\in \mathbb{R}^{n \times n}$, $B\in\mathbb{R}^{m\times m}$.
Do eigendecomposition of $A=U_{A}D_{A}U_{A}^{-1}$, $B=U_{B}D_{B}U_{B}^{-1}$, the above equation is equivalent to
$$
\begin{aligned}
U_{B}^{-1}TAU_{A}^{-1} - U_{B}^{-1}BTU_{A}^{-1}=U_{B}^{-1}CU_{A}^{-1}
\end{aligned}
$$
It's reduced to 
$$
\begin{aligned}
\bar{T}D_{A}-D_{B}\bar{T}=\bar{C}
\end{aligned}
$$
Then
$$
\begin{aligned}
(\alpha_{j}-\beta_{i})t_{i,j}=c_{i,j}
\end{aligned}
$$
It's easy to see that as long as $a_{j}\neq \beta_{i}$, namely $A$ and $B$ shares no common eigen-values, there's always a solution of $t_{i,j}$.

## Reference
- [Observing the State of a Linear System](https://ieeexplore.ieee.org/document/4323124)
- [Constrained Matrix Sylvester Equations](https://www.cs.umd.edu/users/oleary/reprints/j34.pdf)