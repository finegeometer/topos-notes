# Classes of Topos

| Topos Name | Topos | Theory Name | Theory |
|-|-|-|-|
| [Sheaves on a site](./toposes/sheaf_site.md) | $$\Sh(\C,\J)$$ | $\J$-continuous flat functors | [See here](toposes/sheaf_site.md) |
| [Sheaves on a posite](./toposes/sheaf_posite.md) | $$\Sh(P,\triangleleft)$$ | Cover-respecting filters | $$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
    \\ &\forall A \triangleleft\mathcal{B},& \red{A}                                &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$ |
| [Sheaves on a locale]((./toposes/sheaf_locale.md)) | $$\Sh(L)$$ | Points of $L$ | $$\small\begin{align*}
    &\forall A \in O(L),                   &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \red{\top}
    \\ &\forall A, B \in O(L),             & \red{A}, \red{B}                       &\vdash \red{A \wedge B}
    \\ &\forall \mathcal{B} \subseteq O(L),& \red{\bigvee_{B \in \mathcal{B}} B}    &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$ |
| [Presheaves on a category](./toposes/presheaf_category.md) | $$\Psh(\C)$$ | Flat functors | [See here](toposes/presheaf_category.md) |
| [Presheaves on a poset](./toposes/presheaf_poset.md) | $$\Psh(P)$$ | Filters | $$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
\end{align*}$$ |
| [Slice](./toposes/slice.md) | $$\Set_{/X}$$ | Elements of $X$ | $$\small\vdash x : \blue{X}$$ |
| [Weighted 2-Limits](./toposes/limit.md) | $$\varprojlim_W F$$ | Pseudonatural transformations from $W$ to the 2-functor mapping $d$ to the category of models of $F d$ | |
| [Products](./toposes/limit.md#products) | $$\prod_{i \in I} \E_i$$ | Concatenation of theories | $$\small \forall i \in I, T_i \\ \text{where \(\E_i\) classifies \(T_i\)}$$ |
| [Weighted 2-Colimits](./toposes/colimit.md) | $$\varinjlim_W F$$ | TODO | TODO |
| [Coproducts](./toposes/colimit.md#coproducts) | $$\coprod_{i \in I} \E_i$$ | Disjunction of theories | $$\small\begin{align*}
    &    \forall i    \in I, &          &\vdash P_i : \Prop
    \\ &                     &          &\vdash \bigvee_{i \in I} P_i
    \\ & \forall i, j \in I, & P_i, P_j &\vdash \blue{i = j}
    \\ & \forall i    \in I, & P_i      &\vdash T_i
\end{align*} \\ \text{where \(\E_i\) classifies \(T_i\)}$$ |
