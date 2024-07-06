# Monoidal Structure

Let $\C$ be any monoidal category, and consider its topos of presheaves. Let $\yo : \C \to \Psh(\C)$ be the Yoneda embedding.

We have a monoidal closed structure on $\Psh(\C)$, given by Day convolution.

$$\begin{align*}
    I &= c \mapsto \yo(I)
    \\ X * Y &= c \mapsto \int^{c_1, c_2 \in \C} \hom_\C(c, c_1 \otimes c_2) \times X(c_1) \times Y(c_2)
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

## Useful Facts

- Just like $\to$, $\wand$ preserves limits in the second argument, and maps colimits in the first to limits. For example:
    $$\begin{align*}
        &W \vdash (X + Y) \wand Z
        \\ &\iff X + Y \vdash W \wand Z
        \\ &\iff (X \vdash W \wand Z) \times (Y \vdash W \wand Z)
        \\ &\iff (W \vdash X \wand Z) \times (W \vdash Y \wand Z)
        \\ &\iff W \vdash (X \wand Z) \times (Y \wand Z)
    \end{align*}$$
    - A point of caution: This means $2 \wand X$ is $X \times X$, rather than $X * X$ as you might expect.

### Affine Facts

Suppose the monoidal structure is affine, so $I \cong 1$.

- If a map is defined in the empty context, it doesn't matter whether it uses $\to$ or $\wand$.
$$1 \vdash A \to B \iff A \vdash B \iff I \vdash A \wand B$$
- $A * B$ maps into $A \times B$. I suspect this is an injection, making $A * B$ a subset of $A \times B$.
- $A \to B$ maps into $A \wand B$. I suspect this is an surjection, making $A \wand B$ a quotient of $A \to B$.
- For any $f, g : (a : A) \to B a$, we have $(a : A) * (f(a) = g(a)) \cong (a : A) \times (f(a) = g(a))$.
    So we don't have to worry about which product we use while defining subsets by equations. We can just write $\{x \in X | \dots\}$.
    - In the forward direction, we have the inclusion map.
    - In the backwards direction, it suffices to prove $(a : A) \to (x, y : B(a)) \to x = y \to A * (x = y)$.
        By the $=$-eliminator, it in turn suffices to prove $(a : A) \to (x : B(a)) \to A * (x = x)$.
        And that's easy.

