# Classifying Topos for Upper Dedekind Reals

This is a continuous version of the [topos of trees](./trees.md).
That one is presheaves on the poset of naturals;
this one is *sheaves* on the *posite* of *reals*.
Or rationals; it doesn't really matter.

This is also the classifying topos for upper dedekind reals.

We also consider the variation $\Sh(\RR^+)$ on nonnegative reals.

TODO

## Morphisms

For any $t \in \RR^+$, we have a map from $\Set \to \Sh(\RR^+)$, given by substituting $t$ for the generic real number.
- Its inverse image is interpreted as "Sample at time $t$".
- Its direct image is interpreted as $A \mapsto \begin{cases} 1 & \text{before time t} \\ A & \text{after time t} \end{cases}$.

If $t = 0$, this is left adjoint to the terminal geometric morphism.
- The terminal morphism's inverse image is interpreted as "Constant for all time".
- The terminal morphism's direct image is interpreted as "Sample at time $0$".

---

For any $t \in \RR^+$, we have the following adjoint pair of endomorphisms on $\Sh(\RR^+)$.
$$ (x := \max(0, x-t)) \dashv (x := x+t) $$
This yields an adjoint triple of functors:
- "Skip forward by time $t$."
- "Push it back by time $t$, spreading out the now."
- TODO

