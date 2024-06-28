# Sheaves on a site

$$\small\begin{align*}
    &\forall A \in \C,                     &                                        &\vdash \red{A} : \Type
    \\ &\forall f : A \to B,               & x : \red{A}                            &\vdash \red{f}(x) : \red{B}
    \\ &\forall A \in \C,                  & x : \red{A}                            &\vdash \red{\mathrm{id}_A}(x) = x
    \\ &\forall f : A \to B, g : B \to C,  & x : \red{A}                            &\vdash \red{g}(\red{f}(x)) = \red{(g \circ f)}(x)
    \\ &                                   &                                        &\vdash \bigvee_{A \in \C} \exists x : \red{A}, \top
    \\ &\forall A, B \in \C,               & x : \red{A}, y : \red{B}               &\vdash \bigvee_{\substack{C \in \C \\ f : C \to A \\ g : C \to B}} \exists z : \red{C}, \red{f}(z) = x \land \red{g}(z) = y
    \\ &\forall f, g : A \to B,            & x : \red{A}, \red{f}(x) = \red{g}(x)   &\vdash \bigvee_{\substack{C \in \C \\ h : C \to A \\ f \circ h = g \circ h}} \exists z : \red{C}, \red{h}(z) = x
    \\ &\forall \{f_i : B_i \to A\} \in \J,& x : \red{A}                            &\vdash \bigvee_{i \in I} \exists y : \red{B_i}, \red{f_i}(y) = x
\end{align*}$$

<https://ncatlab.org/nlab/show/theory+of+flat+functors>

## See also

Specializations:
- [Sheaves on a posite](./reference/toposes/sheaf_posite.md)
- [Presheaves on a category](./reference/toposes/presheaf_category.md)
