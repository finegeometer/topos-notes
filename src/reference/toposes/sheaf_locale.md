# Sheaves on a locale

Let $L$ be a locale.

$\Sh(L)$ classifies the theory of completely prime filters on $O(L)$.
This is equivalently the theory of points of $L$.

$$\small\begin{align*}
    &\forall A \in O(L),                   &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \red{\top}
    \\ &\forall A, B \in O(L),             & \red{A}, \red{B}                       &\vdash \red{A \wedge B}
    \\ &\forall \mathcal{B} \subseteq O(L),& \red{\bigvee_{B \in \mathcal{B}} B}    &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$

## See also

Generalizations:
- [Sheaves on a posite](./reference/toposes/sheaf_posite.md)

# Proof

We wish to find the theory that $\Sh(L)$ classifies.

Sheaves over a locale are a special case of [sheaves over a posite](sheaf_posite.md), so let's start there.
$$\small\begin{align*}
    &\forall A \in P,                      &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \bigvee_{A \in P} \red{A}
    \\ &\forall A, B \in P,                & \red{A}, \red{B}                       &\vdash \bigvee_{C \leq A, B} \red{C}
    \\ &\forall A \triangleleft\mathcal{B},& \red{A}                                &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$

We specialize to the case of locales. Since $P = O(L)$ is a meet-lattice, we can simplify rules (3) and (4).
$$\small\begin{align*}
    &\forall A \in O(L),                   &                                        &\vdash \red{A} : \Prop
    \\ &\forall A \leq B,                  & \red{A}                                &\vdash \red{B}
    \\ &                                   &                                        &\vdash \red{\top}
    \\ &\forall A, B \in O(L),             & \red{A}, \red{B}                       &\vdash \red{A \wedge B}
    \\ &\forall \mathcal{B} \subseteq O(L),& \red{\bigvee_{B \in \mathcal{B}} B}    &\vdash \bigvee_{B \in \mathcal{B}} \red{B}
\end{align*}$$
