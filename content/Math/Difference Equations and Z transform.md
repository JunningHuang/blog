---
title: Difference Equations and Z transform
draft: false
tags:
  - DifferenceEquation
  - ZTransform
---
## Difference Equation and Z Transform
Let's recall a bit some basic foundations of differential equations and Laplace transform, the simplest linear ODE:
$$
\begin{aligned}
\dot{x}=ax+bu
\end{aligned}
$$

Laplace transform is invented to solve such a DE, take the Laplace transform, we have
$$
\begin{aligned}
sX(s)=aX(s)+bU(s)
\end{aligned}
$$
Rearrange we have 
$$
\begin{aligned}
\frac{X(s)}{U(s)}=\frac{b}{s+a}
\end{aligned}
$$
we can see that the Laplace transform helps us to ease the computation of convolution into product and then do inverse Laplace transform. 

Now let's move on to difference equations
$$
\begin{aligned}
x[n]=ax[n-1]+bu[n]
\end{aligned}
$$
Take the z transform,
$$
\begin{aligned}
X(z)=az^{-1}X(z)+bU(z)
\end{aligned}
$$
Rearrange we have,
$$
\begin{aligned}
\frac{X(z)}{U(z)}=\frac{b}{1-az^{-1}}
\end{aligned}
$$
let $b=1-\gamma$ and $a=\gamma$, the difference equation becomes
$$
\begin{aligned}
x[n]=\gamma x[n-1]+(1-\gamma) u[n]
\end{aligned}
$$

## Integral by parts
Integral by parts not only works for continuous functions, there's a analog for discrete functions. Let's recall integral by parts for indefinite integral first,
$$
\begin{aligned}
\int u \, dv = uv - \int  v\, du  
\end{aligned}
$$
for definite integral,,
$$
\begin{aligned}
\int_{a}^b  u\, dv = uv|_{a}^b - \int_{a}^b v\, du 
\end{aligned}
$$
The analog for discrete function would be 
$$
\begin{aligned}
\sum_{0}^{N} f[n](g[n+1]-g[n]) = f[N+1]g[N+1]-f[0]g[0]-\sum_{0}^N g[n+1](f[n+1]-f[n])
\end{aligned}
$$

Life is short, let's skip the proof.