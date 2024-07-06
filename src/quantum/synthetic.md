# Synthetic Notions

We consider the classifying topos of star-rings. The generic star-ring, $C$, is $\yo(\ZZ[x, x^*])$.

We compute:
$$\begin{align*}
    C * C &= \yo(\ZZ[x,x^*]) * \yo(\ZZ[y,y^*])
    \\ &= \yo(\ZZ[x,x^*] \otimes \ZZ[y,y^*])
    \\ &= \yo(\ZZ[x,x^*,y,y^*,[x,y]=[x^*,y]=[x,y^*]=[x^*,y^*]=0])
    \\ &= \{(x,y) \in C^2 \mid [x,y]=[x^*,y]=[x,y^*]=[x^*,y^*]=0\}
\end{align*}$$

More generally, $X * Y$ tends to be the subset of $X \times Y$ where, intuitively, "everything in $X$ commutes with everything in $Y$".
In the case of $(x,y) : C * C$, that captures commutativity of $x$ and $y$, but also of $x^*$ and $y$.

## Quasicoherence.

Theorem 4.10 of [this paper](https://rawgit.com/iblech/internal-methods/master/paper-qcoh.pdf)
gives us a way to understand function types involving $C$.
For instance, we find that every function $f : C \to C$ is a noncommutative polynomial in both $x$ and $x^*$,
which have coefficients *interleaved* with the variables in each monomial.

I expect there to be an analogous theorem for monoidal function types.
Something to the effect of $A \cong ((A \stackrel{R\text{-alg}}{\wand} R) \wand R)$.
This would make every function $f : C \wand C$ a noncommutative polynomial in both $x$ and $x^*$,
but with only one coefficient attached to each monomial.
The idea is that $x$ and $x^*$ commute past the coefficients, even if they don't commute past each other.

For the rest of this exploration, I will simply assume this hypothesized theorem works.

## Basics

There's quite a lot of subtlety to every aspect of this theory. So let's start from the basics.

We begin with the generic star-ring, $C$. We tend to treat as if it were the complex numbers.

Using complex conjugation, we can define the real and imaginary axes.
$$\begin{align*}
    R &= \{x \in C | x^* = x\}
    \\ I &= \{x \in C | x^* = -x\}
\end{align*}$$

If we assume $\frac{1}{2}$ exists, we can define the real and imaginary parts of a number.
$$\begin{align*}
    \Re &: C \to R & \Im &: C \to I
    \\ \Re&(x) = \frac{x + x^*}{2} & \Im&(x) = \frac{x - x^*}{2}
\end{align*}$$

This in fact exhibits $C$ as the product $R \times I$. The backwards map $R \times I \to C$ is simply addition.
And of course, if we're given a square root of $-1$, we can construct an isomorphism $R \cong I$.

But it's interesting to note that $C \cong R \times I$, rather than $R * I$.
The real and imaginary parts don't have to commute with each other!

A bit more thought shows that $[\Re(x),\Im(x)] = \frac{[x^*,x]}{2}$.
So the noncommutativity of the real and imaginary parts is captured by the value of $[x^*,x]$.

This means we don't have $x^*x = xx^*$ in general. So we should be a bit careful when defining the magnitude of a complex number.
Assuming $\frac{1}{2}$ exists, we say $\lVert x \rVert^2 = \frac{x^*x + xx^*}{2}$.

Fun facts about commutators:
- If $x \in C$, $[x,x^*] \in R$.
- If $x, y \in R$ or $x,y \in I$, $[x,y] \in I$.
- If $x \in R$ and $y \in I$, or vice versa, $[x,y] \in R$.

Finally, quasicoherence gives us a useful understanding of function types, like $C \wand C$.
- $C \wand C \cong C[x,x^*]$.
- $R \wand C \cong C[x]$
    - $R \wand R \cong R[x]$
    - $R \wand I \cong I[x]$
- $I \wand C \cong C[x]$
    - $I \wand R \cong I[x]$
    - $I \wand I \cong R[x]$

$C \wand R$ and $C \wand I$ are a bit more subtle; rather than simply restrict the coefficients to be real, they force *different* coefficients to be conjugate to each other.

## Positivity

TODO

## Calculus

Now for the *differential* part of synthetic differential geometry.

Let $D = \{x \in R | x^2 = 0\}$. Quasicoherence says functions $D \wand C$ are linear maps $\epsilon \mapsto a + b\epsilon$, where $(a, b) \in C \times C$.
Using this, we define the derivative of $f : R \wand C$ at $x : R$ to be the unique $b$ such that $(\epsilon : D) \wand f(x + \epsilon) = f(x) + b\epsilon$.

We can do the same thing in the imaginary direction.
Let $iD = \{x \in I | x^2 = 0\}$. Quasicoherence says functions $iD \wand C$ are linear maps $\epsilon \mapsto a + b\epsilon$, where $(a, b) \in C \times C$.
Using this, we define the "imaginary derivative" of $f : I \wand C$ at $x : I$ to be the unique $b$ such that $(\epsilon : D) \wand f(x + \epsilon) = f(x) + b\epsilon$.

To fully capture the derivative of a function $C \wand C$, we should compute both the real and imaginary derivatives, independently.

It's interesting that this classifying topos naturally led to postulating a space of *complex* numbers, yet the functions $C \wand C$ are only *real*-differentiable!

---

More generally, suppose we have a function $f : X \wand Y$.
This lifts to a function $(D \wand X) \wand (D \wand Y)$.
Defining $T_x X = \{f : D \wand X \mid f(0) = x\}$, we have a function $((x : X) \times T_x X) \wand ((y : Y) \times T_y Y)$.
The first component just returns $f(x)$, so the second is a function $Df : ((x : X) \times T_x X) \wand (T_{f(x)} Y)$.

This works no matter *what* kind of types $X$ and $Y$ are! You just have to be careful about their tangent spaces.
Common types like $C$, $R$, $I$, et cetera are their own tangent spaces, but other types might be weirder.

## Vector Spaces

A vector space is just a set with a couple operations, satisfying a number of axioms.
But "a couple of operations" is trickier than it sounds. Should we require $+ : V \to V \to V$, or $V \wand V \wand V$? Or a mix of the two?

Why do we care about vector spaces? Because we want velocity vectors. Acceleration vectors. Force vectors. Et cetera.

All of these live in tangent spaces to spacetime. So we should understand the tangent space of a manifold, and see what kind of vector space it really is.

Elements of a tangent space $T_x M = \{f : D \wand M \mid f(0) = x\}$ can be scaled as follows:
$$\mathrm{scale}(a, f) = \epsilon \mapsto f(a\epsilon)$$

So let's analyze which function types use $\to$ vs. $\wand$.
- The resulting function should have type $D \wand T_x M$, so $\epsilon$ commutes with everything in the context.
    - That's good, because we need that to show $a\epsilon \in D$.
- Since $f : D \wand T_x M$, and we apply it to $a\epsilon$, $f$ must commute with $a$.
- I see no reason to insist that $f$ or $a$ commute with $M$ or $x$.

So:
$$\mathrm{scale} : R * T_x M \to T_x M$$

Now for addition.

$T_x M$ only supports addition when $M$ is "nice". Whatever the equivalent to microlinearity is.
So let's pick a simple, but nontrivial, example. Let $M = \{x \in C \mid [x,x^*] = 1\}$.

An element of $T_x M$ will have the form $f(\epsilon) = m\epsilon + x$,
and some calculation shows we should require $[m, x^*] \in I$.
The sum of $\epsilon \mapsto m_1\epsilon + x$ and $\epsilon \mapsto m_2\epsilon + x$ should be $\epsilon \mapsto (m_1 + m_2)\epsilon + x$.
This result will automatically satisfy the required condition, so there appears to be no reason to require any form of commutativity.

$$+ : T_x M \times T_x M \to T_x M$$

---

Based on this analysis, I propose that an $R$-vector space should have the following interface:
$$\begin{align*}
    0 &\in V
    \\ \mathrm{+} &: V \times V \to V
    \\ \mathrm{scale} &: R * V \to V
\end{align*}$$
