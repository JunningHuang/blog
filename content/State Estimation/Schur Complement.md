---
title: Schur Complement
draft: false
tags:
  - Algebra
author:
---
## Overview
In this note I would review the idea of Schur complement and its application in calculating the matrix inverse lemma and some properties.

## Schur Complement
Schur complement naturally comes out when we do Gaussian elimination for an invertible square matrix $M=\begin{bmatrix}A&B\\ C&D\end{bmatrix}$, where $A,B,C,D$ are $p\times p$, $p\times q$, $q\times p$, $q\times q$. First we do column multiplication, which is the left multiplication to get the upper triangular form. 
$$
\begin{aligned}
\begin{bmatrix}A&B\\ C&D\end{bmatrix} 
\begin{bmatrix}I_p&0\\ -D^{-1}C&I_q\end{bmatrix}=
\begin{bmatrix}A-BD^{-1}C&B\\0 &D\end{bmatrix}
\end{aligned}
$$
The first entry of the upper triangular form is Schur complement. Continue the Gaussian elimination, we have
$$
\begin{aligned}
\begin{bmatrix}I_p & -BD^{-1} \\ 0 & I_q  \end{bmatrix}
\begin{bmatrix}A&B\\ C&D\end{bmatrix} 
\begin{bmatrix}I_p&0\\ -D^{-1}C&I_q\end{bmatrix}&=
\begin{bmatrix}I_p & -BD^{-1} \\ 0 & I_q  \end{bmatrix}
\begin{bmatrix}A-BD^{-1}C&B\\0 &D\end{bmatrix}\\
&=\begin{bmatrix}A-BD^{-1}C&0\\0 &D\end{bmatrix}\\
\end{aligned}
$$
Rearrange we have a UDL decomposition
$$
\begin{aligned}
\begin{bmatrix}A&B\\ C&D\end{bmatrix} 
=\begin{bmatrix}I_p & BD^{-1} \\ 0 & I_q  \end{bmatrix}
\begin{bmatrix}A-BD^{-1}C&0\\0 &D\end{bmatrix}
\begin{bmatrix}I_p&0\\ D^{-1}C&I_q\end{bmatrix}
\end{aligned}
$$
Usually, we write $M /D=A-BD^{-1}C$ as the symbol for Schur complement.
## Application of Schur Complement 
The common application of Schur Complement is to calculate the matrix inverse:
$$
\begin{aligned}
\begin{bmatrix}A&B\\ C&D\end{bmatrix}^{-1}
&= 
\begin{bmatrix}I_p&0\\ -D^{-1}C&I_q\end{bmatrix}
\begin{bmatrix}(M / D)^{-1}&0\\0 &D^{-1}\end{bmatrix}
\begin{bmatrix}I_p & -BD^{-1} \\ 0 & I_q  \end{bmatrix}\\
&=
\begin{bmatrix}(M /D)^{-1} & 0 \\-D^{-1}C(M /D)^{-1} &D^{-1}\end{bmatrix}
\begin{bmatrix}I_p & -BD^{-1} \\ 0 & I_q  \end{bmatrix}\\
&=
\begin{bmatrix}(M /D)^{-1} & -(M /D)^{-1}BD^{-1} 
\\-D^{-1}C(M /D)^{-1} &D^{-1}+D^{-1}C(M /D)^{-1}BD^{-1}\end{bmatrix}
\end{aligned}
$$
The above formula is called matrix inversion lemma, it has a lot of application in calculating the conditional and marginal distribution of the Gaussian distribution.

Another application of the Schur complement lemma is in matrix inequality, it's an useful tool to construct a linear matrix inequality for conic programming. The properties is consider the case when $M$ is a symmetric and real matrix, given by
$$
\begin{aligned}
M=\begin{bmatrix}A &B \\B^T & C\end{bmatrix}
\end{aligned}
$$

Then
- If $M \succ 0$ and $C$ is invertible, then $M/C \succ 0$ and $C\succ 0$
And if we use the following identity
$$
\begin{aligned}
\begin{bmatrix}
A &B \\B^T & C
\end{bmatrix}\succ 0 \Leftrightarrow 
\begin{bmatrix}
C & B^{T}\\ B & A
\end{bmatrix}\succ 0
\end{aligned}
$$
This can be easily verified by taking the UDL decomposition of the matrix 
$$
\begin{aligned}
\begin{bmatrix}
C-B^TA^{-1}B&0  \\
0 & A
\end{bmatrix}
\end{aligned}
$$
Then
- If $M \succ 0$ and $A$ is invertible, then $M / A\succ 0$ and $A\succ 0$.  

One can check the paper [LMI for physically consistent SysID]([Linear matrix inequalities for physically consistent inertial parameter identification: A statistical perspective on the mass distribution](https://ieeexplore.ieee.org/abstract/document/7987066/)), the authors use the Schur complement to construct a conic programming problem.

## Reference
- [Schur Complement Wiki](https://en.wikipedia.org/wiki/Schur_complement#cite_note-von_Mises_1964-8)