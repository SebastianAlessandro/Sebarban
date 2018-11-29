# FDA Exercises

## Some Exercises

### 1
Using the definition of singular value given in the lecture notes, show that
\[
\sigma_1(A) \geq \sigma_2(A) \geq \cdots \geq \sigma_r(A)
\]

_Solution:_

From the definition the first singular vector is given by
\[
v_1 = \arg\max_{||v||_2 = 1} ||Av||_2
\]
and $\sigma_1(A) = ||Av_1||_2$, hence
\[
\sigma_1(A) = \max_{||v||_2 = 1} ||Av||_2.
\]
In order to obtain the other singular values we have to solve
\[
\sigma_k(A) = \max ||Av||_2
\]
over $\{v \in V : ||v||_2 = 1 \text{ and } \langle v_1, v \rangle = 0, \cdots, \langle v_{k-1}, v \rangle = 0\}$. So we are looking for the maximum of a smaller set and precisely the set obtained removing the maxima at each step.

### 2
Given the matrix
\[
A = \begin{pmatrix}
17 & 8 \\
8 & 17
\end{pmatrix}
\]
determine the SVD (by hand) and express $A$ in the form
\[
A = \sum_{i=1}^r \sigma_i(A) u_i v_i^T
\]

_Solution:_

In matrix notation the singular value decomposition reads $A = U \Sigma V^H$.
We observe that the matrix $A$ is real valued, square and symmetric so $U = V$, $A = V \Sigma V^T$ and the singular values are the eigenvalues of $A$.

> Finding the Eigenvalues
\[
\begin{aligned}
0 & = \det(A-\lambda I) \\
& = (17-\lambda)^6 - 8^2 \\
& = (25 - \lambda)(9-\lambda)\\
\lambda_1 & = 25\\
\lambda_2 & = 9
\end{aligned}
\]
> Eigenvectors, i.e. $v_i \in \mathbb{R}^2$ such that $Av_i = \lambda_i v_i$ and $||v_i || = 1$
\[
Av_i = \lambda_i v_i \iff (A - \lambda_i I)v_i = 0
\]
Thus for the first eigenvector we have
\[
(A - \lambda_1 I) =
\begin{pmatrix}
-8 & 8 \\
8 & -8
\end{pmatrix}
\]
and
\[
v_1 =
\begin{pmatrix}
\frac{1}{\sqrt{2}} \\
\frac{1}{\sqrt{2}}
\end{pmatrix}
\]
Similarly for $\lambda_2$, getting
\[
v_2 =
\begin{pmatrix}
\frac{1}{\sqrt{2}} \\
-\frac{1}{\sqrt{2}}
\end{pmatrix}
\]
> Finally $U = V = \begin{pmatrix}
\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\
\frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}}
\end{pmatrix}$ and $\Sigma = \begin{pmatrix}
25 & 0 \\
0 & 9
\end{pmatrix}$

### 3
Let $A$ be an $m\times n$-matrix and $A^\dagger$ the Moore-Penrose pseudoinverse of $A$. Show that the following statements, known as the Moore-Penrose-conditions, hold:

* $A A^\dagger A = A$
* $A^\dagger A A^\dagger = A^\dagger$
* $(AA^\dagger)^H = A A^\dagger$
* $(A^\dagger A)^H = A^\dagger A$

Using the definition and Hermitian/Transpose properties.

### 4

Given the linear system
\[
\begin{aligned}
2 x_1 + 3 x_2 -  x_3 & = 1 \\
3 x_1 - 4 x_2 + x_3 & = 2 \\
x_1 + x_2 - x_3 & = 3 \\
4 x_1 + 2 x_2 + 2 x_3 & = 4
\end{aligned}
\]
find a vector $x^*$ in an appropriate subspace $V$ of $\mathbb R^4$ that minimises the orthogonal projection of the vector $y = (1, 2, 3, 4)^T$ onto V.

* We observe that the system $A x = y$ is overdetermined; need for approximated solutions that minimise the mismatch $||Ax - y ||_2$.
* Vectors solving the linear system belong to the $ker$ of the linear application associated to $A$ and form a subspace $V$ of $\mathbb{R}^4$.
* The problem can be solved using **Prop. 2.12** (or Corollary 2.13)
  > the convex optimisation problem ${\arg\min}_{x \in \mathcal M} ||x||_2$ has the unique solution $x^* = A^\dagger y$
\[
A = \begin{pmatrix}
2 & 3 & -1 \\
3 & -4 & 1 \\
1 & 1 & -1 \\
4 & 2 & 2
\end{pmatrix} \qquad
y =
\begin{pmatrix}
1 \\ 2 \\ 3 \\ 4
\end{pmatrix}
\]
We have defined the Moore-Penrose Pseudo Inverse as
\[
A^{\dagger} = V \Sigma^{-1} U^H
\]
where $U, \Sigma, V$ are the usual matrix found through the SVD, which can be solved by means of the power method.
