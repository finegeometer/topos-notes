# Geometric Morphisms, Transformations, and Adjunctions

A geometric morphism from $\Set[T_1]$ to $\Set[T_2]$ is given by a $T_2$-model, internal to $\Set[T_1]$.
And a geometric transformation is a morphism of models.

However, there's a more useful framing.

A geometric morphism from $\Set[T_1]$ to $\Set[T_2]$ is, by Yoneda, a functor from $\E \to \Set[T_1]$ to $\E \to \Set[T_2]$ that is itself functorial in $\E$.
In other words, a functor from $T_1$-models to $T_2$-models, *functorially* internal to an arbitrary topos.

If the map from $T_1$-models to $T_2$-models is written in geometric logic, that suffices to ensure the functoriality in $\E$.
(TODO: Why?)

So a geometrically-defined functor from $T_1$-models to $T_2$-models defines a morphism from $\Set[T_1]$ to $\Set[T_2]$.
Analogously, a geometrically-defined natural transformation between such functors defines a geometric transformation.

# Adjunctions

Using the above, a geometrically-defined *adjunction* between the $T_1$-models and $T_2$-models defines an adjunction of geometric morphisms.

It's worth noting, though, that adjunctions between toposes work backwards from what you might expect.
If a geometric morphism has a left adjoint, that means its direct image has a further right adjoint.
And if a geometric morphism has a right adjoint, that means its inverse image has a finite-limit-preserving left adjoint.

# Global Sections

An important special case is that of morphisms to [the topos of sets](../toposes/sets.md).
In that case, $T_2$ is the empty theory, so its category of models is the terminal category.

The unique morphism from $T_1$ into the terminal category gives rise to the global sections functor.
This morphism's left and right adjoints would pick out the initial and terminal $T_1$-models, respectively.

So:
- If there is an initial $T_1$-model, the global sections functor has a left adjoint, so $\Set[T_1]$ is a local topos.
- If there is an terminal $T_1$-model, the global sections functor has a right adjoint.
- If both exist, $\Set[T_1]$ is cohesive. But this not a necessary condition; cohesion only requires strong connectedness, not total connectedness.
- If the category of $T_1$-models has a zero object, $\Set[T_1]$ is infinitesimal cohesive.

All of these assume the relevent $T_1$-models are defined within geometric logic.
