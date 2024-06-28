# Weighted 2-Colimits

The 2-category of toposes is supposedly cocomplete. But do not yet know how to construct colimits.

So let's analyze a special case.

<!-- Let $W : D^{\mathrm{op}} \to \Cat$ and $F : D \to \Topos$.
Let $L$ be $W$-weighted colimit of $F$.

Weighted colimits are defined by the the condition that $\Topos(L, \E) \cong [D^{\mathrm{op}}, \Cat](W, \Topos(F -, \E))$.
This means models of any theory $T$, internal to $L$, correspond to pseudonatural transformations from $W$ to the 2-functor mapping $d$ to the category of models of $T$ inside $F d$. -->

## Coproducts

Let $\{T_i | i \in I\}$ be a collection of theories.
Then the coproduct of the classifying topoi, $\coprod\limits_{i \in I} \Set[T_i]$, classifies the following theory.
$$\small\begin{align*}
    &    \forall i    \in I, &          &\vdash P_i : \Prop
    \\ &                     &          &\vdash \bigvee_{i \in I} P_i
    \\ & \forall i, j \in I, & P_i, P_j &\vdash \blue{i = j}
    \\ & \forall i    \in I, & P_i      &\vdash T_i
\end{align*}$$

**Proof:**
$$\small\begin{align*}
    &\text{This theory}
    \\ &= \left(P : \coprod_{i \in I} Prop\right)
        \times \left(\bigvee_{i \in I} P_i\right)
        \times \left(\bigwedge_{i, j \in I} P_i \land P_j \to \blue{i = j}\right)
        \times \left(\prod_{i \in I} P_i \to T_i\right)
    \\ &= \left(P : \coprod_{i \in I} Type\right)
        \times \left(\prod_{i \in I} \left(x, y : P_i\right) \to x = y\right)
        \times \left(\bigvee_{i \in I} P_i\right)
        \times \left(\prod_{i, j \in I} P_i \land P_j \to \blue{i = j}\right)
        \times \left(\prod_{i \in I} P_i \to T_i\right)
    \\ &= \left(P : \coprod_{i \in I} Type\right)
        \times \left(\left(x, y : \coprod_{i \in I} P_i\right) \to x = y\right)
        \times \left(\bigvee_{i \in I} P_i\right)
        \times \left(\prod_{i \in I} P_i \to T_i\right)
    \\ &= \left(\Sigma P : \Type\right)
        \times(f : \Sigma P \to \blue{I})
        \times \left(\left(x, y : \Sigma P\right) \to x = y\right)
        \times \left(\exists x : \Sigma P. \top\right)
        \times \left((x : \Sigma P) \to T_{f(x)}\right)
    \\ &= \left(\Sigma P : \Prop\right)
        \times(f : \Sigma P \to \blue{I})
        \times \Sigma P
        \times \left((x : \Sigma P) \to T_{f(x)}\right)
    \\ &= (f : 1 \to \blue{I}) \times \left((x : 1) \to T_{f(x)}\right)
    \\ &= (i : \blue{I}) \times T_i
    \\ &= \coprod_{i \in I} T_i
\end{align*}$$

And as discussed [here](../properties/adjunction.md), the colimit diagram for these theories lifts to a colimit diagram in topoi.

### Properties

Let $\left\{\iota_i : \E_i \to \coprod\limits_{j \in I} \E_j \middle| i \in I\right\}$ be the canonical injections.

**Theorem:** Internally to $\coprod\limits_{i \in I} \E_i$, we have $(\iota_i)_*(\iota_i)^* A \cong P_i \to A$.

**Proof:** Treating $\coprod\limits_{i \in I} \E_i$ as our base topos, $\E_i$ classifies the theory $\vdash P_i$.
This is a [slice topos](./toposes/slice.md), so the result from that page applies.

**Corollary:** Internally to $\coprod\limits_{i \in I} \E_i$, we have $A = \coprod\limits_{i \in I} (\iota_i)_*(\iota_i)^* A$.

**Proof:** $\coprod\limits_{i \in I} (\iota_i)_*(\iota_i)^* A \cong \coprod\limits_{i \in I} P_i \to A \cong \left(\prod\limits_{i \in I} P_i\right) \to A \cong 1 \to A \cong A$.

## See also

Specializations:
- [Initial Topos](./reference/toposes/initial.md)
