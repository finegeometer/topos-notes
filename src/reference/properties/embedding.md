# Geometric Embeddings

A geometric morphism $f : \F \to \E$ is an [embedding](https://ncatlab.org/nlab/show/geometric+embedding)
iff $\epsilon : f^* f_* A \to A$ is an equivalence.
We say $\F$ is a [subtopos](https://ncatlab.org/nlab/show/subtopos) of $\E$.

**Theorem**: If a theory is composed only of axioms, its classifying topos is a subtopos of $\Set$.

**Proof:** Work internally to the supposed subtopos.

TODO

**Corollary**: If $T$ is a theory, and $T'$ an extension that only adds axioms, then $\Set[T']$ is a subtopos of $\Set[T]$.

**Proof:** Apply the previous theorem, with $\Set[T]$ as your base topos.
