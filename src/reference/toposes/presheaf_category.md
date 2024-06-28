# Presheaves on a category

Let $C$ be a (small) category. Then $\Psh(C)$ classifies the following theory:

$$\small\begin{align*}
    &\forall A \in \C,                     &                                        &\vdash \red{A} : \Type
    \\ &\forall f : A \to B,               & x : \red{A}                            &\vdash \red{f}(x) : \red{B}
    \\ &\forall A \in \C,                  & x : \red{A}                            &\vdash \red{\mathrm{id}_A}(x) = x
    \\ &\forall f : A \to B, g : B \to C,  & x : \red{A}                            &\vdash \red{g}(\red{f}(x)) = \red{(g \circ f)}(x)
    \\ &                                   &                                        &\vdash \bigvee_{A \in \C} \exists x : \red{A}, \top
    \\ &\forall A, B \in \C,               & x : \red{A}, y : \red{B}               &\vdash \bigvee_{\substack{C \in \C \\ f : C \to A \\ g : C \to B}} \exists z : \red{C}, \red{f}(z) = x \land \red{g}(z) = y
    \\ &\forall f, g : A \to B,            & x : \red{A}, \red{f}(x) = \red{g}(x)   &\vdash \bigvee_{\substack{C \in \C \\ h : C \to A \\ f \circ h = g \circ h}} \exists z : \red{C}, \red{h}(z) = x
\end{align*}$$

This derives from the [theory classified by sheaves](./sheaf_site.md), by choosing $\J$ to be the empty coverage.

## See also

Specializations:
- [Presheaves on a poset](./reference/toposes/presheaf_poset.md)

Generalizations:
- [Sheaves on a site](./reference/toposes/sheaf_site.md)
