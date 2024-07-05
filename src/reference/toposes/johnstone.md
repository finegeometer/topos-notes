# Johnstone's Topological Topos

[Johnstone's Topological Topos](https://ncatlab.org/nlab/show/Johnstone%27s+topological+topos) is an important setting for topology,
since it acts as a "convenient category of topological spaces".

See
[these](https://grossack.site/2024/07/03/life-in-johnstones-topological-topos#fnref:8)
[three](https://grossack.site/2024/07/03/topological-topos-2-algebras)
[articles](https://grossack.site/2024/07/03/topological-topos-3-bonus-axioms)
for more information.

This topos is defined as the topos of sheaves on the monoid of continuous endomorphisms on $\NN^\infty$.

The topos classifies the following theory:
$$\small\begin{align*}
    &                           &                                &\vdash X : \Type
    \\ &\forall f,              & x : X                          &\vdash \red{f}(x) : X
    \\ &                        & x : X                          &\vdash \red{\mathrm{id}_A}(x) = x
    \\ &\forall f, g,           & x : X                          &\vdash \red{g}(\red{f}(x)) = \red{(g \circ f)}(x)
    \\ &                        &                                &\vdash \exists x : X, \top
    \\ &                        & x : X, y : X                   &\vdash \bigvee_{f, g} \exists z : X, \red{f}(z) = x \land \red{g}(z) = y
    \\ &\forall f, g,           & x : X, \red{f}(x) = \red{g}(x) &\vdash \bigvee_{\substack{h \\ f \circ h = g \circ h}} \exists z : X, \red{h}(z) = x
    \\ &\forall \{f_i\} \in \J, & x : X                          &\vdash \bigvee_{i \in I} \exists y : X, \red{f_i}(y) = x
\end{align*}$$

Where $U \in \J$ iff $\forall n, (\_ \mapsto n) \in U$ and for any infinite $T \subseteq \NN$, there exists an injective map in $U$ whose image is contained in $T$.


TODO: How to simplify?



