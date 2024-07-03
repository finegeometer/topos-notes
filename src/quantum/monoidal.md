# Monoidal Structure

Let $\C$ be any monoidal category, and consider its topos of presheaves. Let $\yo : \C \to \Psh(\C)$ be the Yoneda embedding.

We have a monoidal closed structure on $\Psh(\C)$, given by Day convolution.

$$\begin{align*}
    X * Y &= c \mapsto \int^{c_1, c_2 \in \C} \hom_\C(c, c_1 \otimes c_2) \times X(c_1) \times Y(c_2)
    \\ X \wand Y &= c \mapsto \int_{c_1 \in \C} X(c_1) \to Y(c \otimes c_1)
\end{align*}$$

The Yoneda embedding preserves the monoidal product.
$$\begin{align*}
    \yo(a) * \yo(b) &= c \mapsto \int^{c_1, c_2 \in \C} \hom_\C(c, c_1 \otimes c_2) \times \hom_\C(c_1, a) \times \hom_\C(c_2, b)
    \\ &= c \mapsto \hom_\C(c, a \otimes b)
    \\ &= \yo(a \otimes b)
\end{align*}$$

And it preserves any monoidal exponentials that happen to exist.

$$\begin{align*}
    \yo(a) \wand \yo(b) &= c \mapsto \int_{c_1 \in \C} \hom_\C(c_1,a) \to \hom_\C(c \otimes c_1,b)
    \\ &= c \mapsto \hom_\C(c \otimes a,b)
    \\ &= c \mapsto \hom_\C(c,b^a)
    \\ &= \yo(b^a)
\end{align*}$$

## Ring

Take the case where $\C^{op} = \Ringfp$, so $\Psh(\C)$ is the classifying topos of rings.
Let $R = \yo(\ZZ[x])$ be the generic ring.

We compute:
$$\begin{align*}
    R * R &= \yo(\ZZ[x]) * \yo(\ZZ[x])
    \\ &= \yo(\ZZ[x] \otimes \ZZ[x])
    \\ &= \yo(\ZZ[x,y,xy=yx])
    \\ &= \{(x,y) \in R^2 \mid xy=yx\}
\end{align*}$$

More generally, $X * Y$ tends to be the subset of $X \times Y$ where, intuitively, "everything in $X$ commutes with everything in $Y$".

A point of caution: $2 \wand X$ is equivalent to $X \times X$, not $X * X$.
More generally, $X + Y \wand Z \cong (X \wand Z) \times (Y \wand Z)$.

### Quasicoherence.

Theorem 4.10 of [this paper](https://rawgit.com/iblech/internal-methods/master/paper-qcoh.pdf)
gives us a way to understand function types involving $R$.

For instance, we find that every function $f : R \to R$ has the form $f(x) = c_{0,0} + c_{1,0} x c_{1,1} + c_{2,0} x c_{2,1} x c_{2,2} + \dots$.
A fully general noncommutative polynomial.

I expect there to be an analogous theorem for monoidal function types.
Something to the effect of $A \cong ((A \stackrel{R\text{-alg}}{\wand} R) \wand R)$

This would have the following consequences:
- Every function $f : R \wand R$ has the form $f(x) = c_0 + c_1 x + c_2 x^2 + \dots$.
- Every function $f : R^2 \wand R$ has the form $f(x) = c + c_1 x + c_2 y + c_{11} x^2 + c_{12} xy + c_{21} yx + c_{22} yy + \dots$.
A noncommutative polynomial, but where the variables commute with the coefficients.
- And every function $f : \{x \in R | x^2 = 0\} \wand R$ has the form $f(x) = a + bx$.
This is essential for synthetic differential geometry, as the "$\to$" version is far less nice.
