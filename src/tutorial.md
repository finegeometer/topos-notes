# Tutorial

From my perspective, topos theory is about exploring different mathematical worlds, and the relationships between them.

Each world follows all the same laws of logic and set theory that we're used to.
We can talk about sets, subsets, functions, et cetera, just like normal.
Well, except for the law of excluded middle; that only holds in a few worlds.

Yet each world is slightly different.
There are worlds in which every function is continuous.
Worlds where infinitesimals exist. (Or at least, don't not exist.)
Worlds which nicely capture the ideas of algebraic geometry.
And of course, there's the "real world", $\Set$.

Each world is called a *topos*.
We can move between these worlds using *geometric morphisms*.
And we can even compare different ways of moving between worlds, using *geometric transformations*.

## Example

As an example, let's look at the "smooth toposes". These satisfy, among other things, the following axioms:
- There is a set of "numbers", called $R$. Numbers can be added, subtracted, and multiplied, and they can be divided by nonzero numbers, all following the usual rules.
- Let $\Delta = \{x \in R | x^2 = 0\}$. Then every function $\Delta \to R$ can be written as $x \mapsto a + bx$, for a unique choice of $a$ and $b$.

The idea is that $\Delta$ is a set of "infinitesimals".
And if a function is only known on an infinitesimal region of $R$,
that's exactly enough information to pick out a tangent line.

This makes calculus easy. The derivative of $f : R \to R$ at $x \in R$ is defined such that $\forall \epsilon \in \Delta, f(x + \epsilon) = f(x) + f'(x) \epsilon$.
To find the derivative of $x^2$, we calculate $(x + \epsilon)^2 = x^2 + 2x\epsilon + \epsilon^2 = x^2 + 2x\epsilon$, so the derivative is $2x$.
We drop the $\epsilon^2$, not because it's "too small to matter" in some awkward-to-prove sense, but because it's *literally zero*!

Same with differential geometry. A tangent vector to a manifold is just a function $\Delta \to M$.
And differential $n$-forms can be seen as functions $M^n \to R$ that are only defined when the inputs are "infinitesimally close together".

One then asks how these smooth toposes relate back to the topos of sets.
And it turns out that for certain "well-adapted" toposes,
the functions $R \to R$ inside the topos correspond *exactly*
to smooth functions $\mathbb{R} \to \mathbb{R}$ in the regular world.
So theorems proven inside the topos can be applied to ordinary, outside-the-topos math.

These ideas are explored much more thoroughly in the books [***Synthetic Differential Geometry***](https://users-math.au.dk/kock/sdg99.pdf)
and [***Synthetic Geometry of Manifolds***](https://tildeweb.au.dk/au76680/SGM-final.pdf), by Anders Kock.

## Side Notes

- There are two, slightly different, meanings of "topos". In this book, I focus on "Grothendieck toposes", not "elementary toposes".
- The plural form of "topos" can be either "toposes" or "topoi". I kind of like "topoi", but I've chosen to stick to "toposes" for simplicity.
