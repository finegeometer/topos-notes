# Weighted 2-Limits

Let $W : D \to \Cat$ and $F : D \to \Topos$.
Let $L$ be $W$-weighted limit of $F$.

Identify toposes with the theories they classify.

Weighted limits are defined by the the condition that $\Topos(\E, L) \cong [D, \Cat](W, \Topos(\E, F -))$.
This means $L$ classifies pseudonatural transformations from $W$ to the 2-functor mapping $d$ to the category of models of $F d$.
This theory is very complicated, but it *is* definable in geometric logic, so we have the required functoriality over $\E$.

Explicitly, treating $F$ as a 2-functor returning categories of models:
- For each $d \in D$ and $w \in W(d)$, an object $\phi(d,w)$ of $F d$.
- For each $d \in D$ and $f : w_1 \xrightarrow{W(d)} w_2$, a model homomorphism $\phi(d,f) : \phi(d,w_1) \to \phi(d,w_2)$.
- For each $\delta : d_1 \xrightarrow{D} d_2$, and $w \in W(d_1)$, an isomorphism $\phi(\delta, w) : \phi(d_2, W(\delta)(w)) \Leftrightarrow F(\delta)(\phi(d_1, w))$.
- For each $d \in D$ and $w \in W(d)$, an equation $\phi(d,1_w) = 1_{\phi(d,w)}$.
- For each $d \in D$, $f : w_1 \xrightarrow{W(d)} w_2$, and $g : w_2 \xrightarrow{W(d)} w_3$, an equation $\phi(d,g \circ f) = \phi(d,g) \circ \phi(f)$.
- For each $\delta : d_1 \xrightarrow{D} d_2$, and $f : w_1 \xrightarrow{W(d)} w_2$, an equation $\phi(\delta, w_2) \circ \phi(d_1, f)$ = $\phi(d_2, f) \circ \phi(\delta, w_1)$.
- For every $\alpha : \delta_1 \xrightarrow{d_1 \xrightarrow{D} d_2} \delta_2$, and $w \in W(d_1)$, an equation $\phi(\delta_2, w) \circ \phi(d_2, W(\alpha)_w) = F(\alpha)_{\phi(d_1, w)} \circ \phi(\delta_1, w)$.
- If $D$ isn't a strict 2-category, even more coherences!

## Unweighted

Suppose $W(d) = \mathbf{1}$ for all $d$. Then the list of conditions simplifies to the following:
- For each $d \in D$, an object $\phi(d)$ of $F d$.
- For each $\delta : d_1 \xrightarrow{D} d_2$, an isomorphism $\phi(\delta) : \phi(d_2) \Leftrightarrow F(\delta)(\phi(d_1))$.
- For each $\delta : d_1 \xrightarrow{D} d_2$, an equation $\phi(\delta) \circ \phi(d_1)$ = $\phi(d_2) \circ \phi(\delta)$.
- For every $\alpha : \delta_1 \xrightarrow{d_1 \xrightarrow{D} d_2} \delta_2$, an equation $\phi(\delta_2) \circ \phi(d_2) = F(\alpha)_{\phi(d_1)} \circ \phi(\delta_1)$.
- If $D$ isn't a strict 2-category, more coherences.

### Products

Now suppose $D$ is the discrete 2-category on a set. All conditions disappear except the first.
So the theory classified by a product of toposes is simply the concatenation of the individual theories.

## Is nLab wrong?

At the time of writing (Jun 26, 2024), [the nLab claims](https://ncatlab.org/nlab/show/Topos#Limits) that "The 2-category Topos is not all that well-endowed with limits".
However, this analysis suggests that $\Topos$ should have all small limits. And the book *Higher Topos Theory*, Corollary 6.3.4.7, says the same holds for $\infty$-topoi.

## See also

Specializations:
- [Topos of Sets](./reference/toposes/sets.md)
