# Topos of Trees

The [*topos of trees*](https://ncatlab.org/nlab/show/topos+of+trees), $\Psh(\omega)$, classifies the theory of
*eventually-true monotonic sequences of propositions*.
$$\small\begin{align*}
       n : \mathbb{N}      &\vdash P_n : \Prop
    \\ n : \mathbb{N}, P_n &\vdash P_{n+1}
    \\                     &\vdash \exists n : \mathbb{N}, P_n
\end{align*}$$

## Properties

- **Localic**: The theory is propositional.

## Morphisms

### Global Sections

The global sections morphism has a right adjoint, but no left adjoint.
$$() \dashv
  (P_n := \top)
$$

### Endomorphisms

There is an adjoint triple of endofunctors given by the following model morphisms:
$$\left(\begin{align*}P_0 &:= \bot \\ P_{n+1} &:= P_n\end{align*}\right) \dashv
  \left(\begin{align*}P_n &:= P_{n+1}\end{align*}\right) \dashv
  \left(\begin{align*}P_0 &:= P_0 \\ P_{n+1} &:= P_n\end{align*}\right)
$$
This exhibits the topos of trees as a cohesive topos over **itself**.

The middle morphism has a natural transformation from the identity. The outer two have natural transformations *to* the identity.

The direct image of the leftmost morphism is the *later modality*, written $\triangleright$.
The natural transformations mentioned above yield a function $\mathrm{next} : A \to \triangleright A$.

**Theorem:** Internally to the topos of trees, there is a function $\mathrm{fix} : (\triangleright A \to A) \to A$, satisfying $\mathrm{fix}(f) = f(\mathrm{next}(\mathrm{fix}(f)))$.

**Proof:** TODO

### TODO: Other

# Proof

The topos of trees is a special case of [presheaves on a poset](./presheaf_poset.md). In fact, a totally-ordered set.
Taking the theory from there, and specializing to $P = \omega$, yields the following.
$$\small\begin{align*}
    &\forall n \in \mathbb{N},&     &\vdash P_n : \Prop
    \\ &\forall m \leq n,     & P_m &\vdash P_n
    \\ &                      &     &\vdash \bigvee_{n \in \mathbb{N}} P_n
\end{align*}$$

Simplifying slightly:

$$\small\begin{align*}
    &\forall n \in \mathbb{N},   &     &\vdash P_n : \Prop
    \\ &\forall n \in \mathbb{N},& P_n &\vdash P_{n+1}
    \\ &                         &     &\vdash \bigvee_{n \in \mathbb{N}} P_n
\end{align*}$$

To simplify farther, I'll take a detour outside geometric logic.
This is acceptable by [Barr's theorem](https://ncatlab.org/nlab/show/Barr%27s+theorem).

Models of the theory are summed up by the following type:
$$\small\left(P : \prod_{n \in \mathbb{N}} \Prop\right) \times \left(\prod_{n \in \mathbb{N}} \pi_n P \to \pi_{n+1} P\right) \times \left(\bigvee_{n \in \mathbb{N}} \pi_n P\right)$$

By the discussion at [External vs. Internal](../ext_int.md), we have the following rewrites.
$$\small\begin{align*}
    &\left(P : \prod_{n \in \mathbb{N}} \Prop\right) \times \left(\prod_{n \in \mathbb{N}} \pi_n P \to \pi_{n+1} P\right) \times \left(\bigvee_{n \in \mathbb{N}} \pi_n P\right)
    \\ &= \left(P : (n : \mathbb{N}) \to \Prop\right) \times \left(\prod_{n \in \mathbb{N}} P(\blue{n}) \to P(\blue{n+1})\right) \times \left(\bigvee_{n \in \mathbb{N}} P(\blue{n})\right)
    \\ &= \left(P : (n : \mathbb{N}) \to \Prop\right) \times \left((n : \mathbb{N}) \to P(n) \to P(n+1)\right) \times \left(\exists n : \mathbb{N}, P(n)\right)
\end{align*}$$

Which describes models of the following.
$$\small\begin{align*}
       n : \mathbb{N}      &\vdash P_n : \Prop
    \\ n : \mathbb{N}, P_n &\vdash P_{n+1}
    \\                     &\vdash \exists n : \mathbb{N}, P_n
\end{align*}$$

<!-- $P_n$, here, is an externally-indexed sequence. 