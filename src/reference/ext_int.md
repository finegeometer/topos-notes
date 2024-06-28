# External vs. Internal

Let $X$ be a set.

Suppose we want to work internally to a topos.
Then there are two ways for our internal statements to depend on $X$.
We can use infinitary operations over $X$, or we can quantify over $\blue{X}$.

These two methods should be equivalent. Let's prove this.

## Dependent Sums vs Coproducts

**Theorem:** $((x : \blue{X}) \times A(x)) \cong \coprod\limits_{x \in X} A(\blue{x})$

**Proof:** The isomorphism maps $(\iota_x(()), a)$ to $\iota_x(a)$, and vice versa.

## Dependent Products vs Products

**Theorem:** $((x : \blue{X}) \to A(x)) \cong \prod\limits_{x \in X} A(\blue{x})$

**Proof:** The isomorphism maps $f$ to a tuple whose $\pi_x$ component is $f(\iota_x(()))$.
In the other direction, a tuple $t$ gets mapped to the function $\iota_x(()) \mapsto \pi_x(t)$.
These are easily seen to be inverses.

## Universals vs Conjunctions

**Theorem:** $\forall x : \blue{X}, P(x) \dashv\vdash \bigwedge\limits_{x \in X} P(\blue{x})$

**Proof:** Immediate from the previous theorem, by treating the propositions as subsingleton sets.

## Existentials vs Disjunctions

**Theorem:** $\exists x : \blue{X}, P(x) \dashv\vdash \bigvee\limits_{x \in X} P(\blue{x})$

**Proof:** TODO

# References

See also: Section 2.5 of [Ingo Blechschmidt's PHD thesis](https://rawgit.com/iblech/internal-methods/master/notes.pdf).