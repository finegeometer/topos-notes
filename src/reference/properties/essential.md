# Essential Geometric Morphisms

An [essential geometric morphism](https://ncatlab.org/nlab/show/essential+geometric+morphism) is one whose inverse image preserves small products.
An [locally connected topos](https://ncatlab.org/nlab/show/locally+connected+topos) is one whose unique morphism to $\Set$ is essential.
(Note that a locally connected geometric morphism is something else.)

I don't yet know how to characterize these, but here are some useful facts.

**Theorem:** Coproducts of essential geometric morphisms are essential.

**Proof:** Let $\{f_i : \E_i \to \F | i \in I\}$ be essential, and let $f : \coprod\limits_{i \in I} \E_i \to \F$ be their coproduct. Let $\{A_j | j \in J\}$ be sets internal to $\F$.
<!-- We will show that $\prod_{j \in J} f^*(A_j) = f^*\left(\prod_{j \in J} A_j\right)$. -->

$$\small\begin{align*}
    & f^*\prod_{j \in J} A_j
    \\ &\cong \coprod\limits_{i \in I} (\iota_i)_*(\iota_i)^* f^*\prod_{j \in J} A_j
    \\ &\cong \coprod\limits_{i \in I} (\iota_i)_*(f_i)^* \prod_{j \in J} A_j
    \\ &\cong \coprod\limits_{i \in I} (\iota_i)_*\prod_{j \in J} (f_i)^*A_j
    \\ &\cong \coprod\limits_{i \in I} \prod_{j \in J} (\iota_i)_*(f_i)^*A_j
    \\ &\cong \coprod\limits_{i \in I} \prod_{j \in J} (\iota_i)_*(\iota_i)^*f^*A_j
    \\ &\cong \coprod\limits_{i \in I} \prod_{j \in J} P_i \to f^*A_j
    \\ &\cong \coprod\limits_{i \in I} P_i \to \prod_{j \in J} f^*A_j
    \\ &\cong \coprod\limits_{i \in I} (\iota_i)_*(\iota_i)^* \prod_{j \in J} f^*A_j
    \\ &\cong \prod_{j \in J} f^*A_j
\end{align*}$$

**Corollary:** Coproducts of locally connected toposes are locally connected.

