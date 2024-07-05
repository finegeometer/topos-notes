# Individual Toposes

| Topos Name | Topos | Theory Name | Theory |
|-|-|-|-|
| [Topos of Sets](./toposes/sets.md) | $$\Set$$ | Trivial theory | $$\small\textit{(no sequents)}$$ |
| [Initial Topos](./toposes/initial.md) | $$\mathbf{1}$$ | Inconsistent theory | $$\small\vdash \bot $$ |
| [Sierpinski Topos](./toposes/sierpinski.md) | $$\Psh(\mathbf{2}) \\ \mathrm{Arr}(\Set)$$ | Propositions | $$\small\vdash P : \Prop $$ |
| [Topos of Trees](./toposes/trees.md) | $$\Psh(\omega)$$ | Eventually-true monotonic sequences of propositions | $$\small\begin{align*}
       n : \mathbb{N}      &\vdash P_n : \Prop
    \\ n : \mathbb{N}, P_n &\vdash P_{n+1}
    \\                     &\vdash \exists n : \mathbb{N}, P_n
\end{align*}$$ |
| [—](./reference/toposes/upper-reals.md) | $$\Sh((\mathbb{R}, \geq)) \\ \Sh((\mathbb{Q}, \geq))$$ | Upper Dedekind Cuts | $$\small\begin{align*}
       q : \mathbb{Q}                              &\vdash P_q : \Prop
    \\ q_1,q_2 : \mathbb{Q}, q_1 \leq q_2, P_{q_1} &\vdash P_{q_2}
    \\                                             &\vdash \exists q \in \mathbb{Q}, P_q
    \\ q_1 : \mathbb{Q},                   P_{q_1} &\vdash \exists q_2 \leq q_1, P_{q_2}
\end{align*}$$ |
| — | $$\Sh(O(\mathbb{R}))$$ | Dedekind Reals | $$\dots$$ |
| [—](./toposes/classify_objects.md) | $$[\FinSet, \Set]$$ | Objects | $$\small\vdash X : \Type $$ |
| [—](./toposes/classify_decidable_objects.md) | $$[\FinSet_\mathrm{mono}, \Set]$$ | Decidable objects | $$\small\begin{align*}
    &                                      &                                        &\vdash X : \Type
    \\ &                                   & x : X, y : X                           &\vdash x \apart y : \Prop
    \\ &                                   & x : X, x \apart x                      &\vdash \bot
    \\ &                                   & x : X, y : X                           &\vdash x \apart y \lor x = y
\end{align*}$$ |
| [Schanuel Topos](./toposes/schanuel.md) | $$[\FinSet_\mathrm{mono}, \Set]_\times$$ | Infinite decidable objects | $$\scriptsize\begin{align*}
    &                                      &                                        &\vdash X : \Type
    \\ &                                   & x : X, y : X                           &\vdash x \apart y : \Prop
    \\ &                                   & x : X, x \apart x                      &\vdash \bot
    \\ &                                   & x : X, y : X                           &\vdash x \apart y \lor x = y
    \\ & \forall n \in \mathbb{N},         & x_0 \dots x_{n-1} : X                  &\vdash \exists y : X, \bigwedge_{i < n} y \apart x_n
\end{align*}$$ |
| [Topos of Species](./toposes/species.md) | $$[\FinSet_0, \Set]$$ | TODO | TODO |
