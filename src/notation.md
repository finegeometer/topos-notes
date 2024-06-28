# Notation

## Infinitary Logic

Infinitary coproducts and products are written as $\coprod\limits_{x \in X} A(x)$ and $\prod\limits_{x \in X} A(x)$.
(Only the former is preserved by geometric morphisms, but the latter is still useful.)

We have injections $\iota_x : A(x) \to \left(\coprod\limits_{x \in X} A(x)\right)$ and projections $\pi_x : \left(\prod\limits_{x \in X} A(x)\right) \to A(x)$.

## External vs Internal

If $X$ is a set in the external logic, then $\blue{X}$ will represent the corresponding set in the internal logic.
(A good definition is $\coprod\limits_{x \in X} 1$.)

If $x \in X$ in the external logic, then $\blue{x} : \blue{X}$ will represent the corresponding value in the internal logic.
(Using the above definition for $\blue{X}$, we have $\blue{x} = \iota_x ()$.)
