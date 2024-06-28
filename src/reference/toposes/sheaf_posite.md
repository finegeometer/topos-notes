# Sheaves on a posite

Let $(P,\triangleleft)$ be a [posite](https://ncatlab.org/nlab/show/posite).

The sheaf category $\Sh(P,\triangleleft)$ classifies filters on $P$ that respect $\triangleleft$
in the sense that whenever $A$ is in the filter and $A\triangleleft\mathcal{B}$, some element of $B$ is in the filter.
$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
    \\ &\forall A \triangleleft\mathcal{B},& \red{A}                                &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$

Interestingly, this is a propositional theory. So this topos is equivalent to [the topos of sheaves over some locale $L$](./sheaf_locale.md).

## See also

Specializations:
- [Sheaves on a locale](./reference/toposes/sheaf_locale.md)
- [Presheaves on a poset](./reference/toposes/presheaf_poset.md)

Generalizations:
- [Sheaves on a site](./reference/toposes/sheaf_site.md)

# Proof

We wish to find the theory that $\Sh(P,\triangleleft)$ classifies.

A posite is a special case of a site. So we start with the theory classified by [sheaves on a site](sheaf_site.md).
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

We specialize to the case of thin categories.
$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Type
    \\ &\forall A \leq B,                  & x : \red{A}                            &\vdash f_{A \to B}(x) : \red{B}
    \\ &\forall A \in P,                   & x : \red{A}                            &\vdash f_{A \to A}(x) = x
    \\ &\forall A \leq B \leq C,           & x : \red{A}                            &\vdash f_{B \to C}(f_{A \to B}(x)) = f_{A \to C}(x)
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \exists x : \red{A}, \top
    \\ &\forall A, B \in P,                & x : \red{A}, y : \red{B}               &\vdash \bigvee_{C \leq A, B} \exists z : \red{C}, f_{C \to A}(z) = x \land f_{C \to B}(z) = y
    \\ &\forall A \leq B,                  & x : \red{A}                            &\vdash \bigvee_{C \leq A} \exists z : \red{C}, f_{C \to A}(z) = x
    \\ &\forall A \triangleleft\mathcal{B},& x : \red{A}                            &\vdash \bigvee_{B \in \mathcal{B}} \exists y : \red{B}, f_{B \to A}(y) = x
\end{align*}$$

Now we simplify.
Rule (6), when specialized to the case $A = B$, implies $x, y : \red{A} \vdash x = y$.
So the types $\red{A}$ are subsingletons, and can be reinterpreted as propositions.

$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &\forall A \in P,                   & \red{A}                                &\vdash \top
    \\ &\forall A \leq B \leq C,           & \red{A}                                &\vdash \top
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \bigvee_{C \leq A} \red{C}
    \\ &\forall A \triangleleft\mathcal{B},& \red{A}                                &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$

Rules (3), (4), and (7) are now redundant.

$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
    \\ &\forall A \triangleleft\mathcal{B},& \red{A}                                &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$

<!-- TODO: Why is this always localic? -->