# Presheaves on a poset

Let $P$ be a poset. Then $\Psh(P)$ classifies the theory of filters on $P$.
$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
\end{align*}$$

This derives from the [theory classified by sheaves on a posite](./sheaf_posite.md), by choosing $\triangleleft$ to be the empty coverage.

There are further small simplifications for special kinds of poset:
- If $P$ has a top element, rule (3) simplifies to $\vdash \red{\top}$.
- If $P$ has binary meets, rule (4) simplifies to $\forall A, B \in P, (\red{A}, \red{B} \vdash \red{A \wedge B})$.
- If $P$ is totally ordered, rule (4) is entirely redundant.

## See also

Specializations:
- [Slice](./reference/toposes/slice.md)
- [Sierpinski Topos](./reference/toposes/sierpinski.md)
- [Topos of Trees](./reference/toposes/trees.md)

Generalizations:
- [Sheaves on a posite](./reference/toposes/sheaf_posite.md)
- [Presheaves on a category](./reference/toposes/presheaf_category.md)
