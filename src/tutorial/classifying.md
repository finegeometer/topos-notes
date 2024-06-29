# How to Build a Topos

So, how do you build a topos? A mathematical world to live in?

The idea is as follows: ***Every geometric theory defines a topos.***

We start by defining certain mathematical constructions to be "geometric".
The intuitive idea is that we ban anything that looks too much like a function or a power set.
So we allow taking cartesian products, and disjoint unions. But we don't allow function sets, or the set of truth values.

On the logical side, we allow the "and" and "or" operations. But not "implies"; that's too much like a function.
We ban negation, because $\neg A$ is defined as $A \to \bot$.
We allow "exists", but not "for all". (I guess a proof of $\forall x. P(x)$ is like a function taking $x$ to a proof of $P(x)$?)

We also allow *infinitely large* "or" operations, but not infinitely large "and" operations.

Now, we define a geometric theory. It's a sequence of axioms. Each axiom says that, under geometrically defined assumptions, you can create:
- A set
- Or a proposition
- Or a value of some geometrically-defined set.
- Or a proof of a geometrically-defined proposition.
Each rule can depend on the preceding ones.

For example, the following sequence of axioms is a geometric theory.
- There is a set, called $N$. (This rule has no assumptions.)
- Given values $x$ and $y$ in $N$, there is a proposition, called $x \apart y$.
- Given $x \in N$, and given a proof of $x \apart x$, there is a proof of $\bot$.
    - This basically says $\neg (x \apart x)$, but in a way that fits into a geometric theory.
- Given values $x$ and $y$ in $N$, there is a proof of $x \apart y \lor x = y$.
- And given any finite list $x_1 \dots x_n \in N$, there is a proof of $\exists y \in N, y \apart x_1 \land \dots y \apart x_n$.

We can write this theory mathematically as follows:
$$\begin{align*}
                                             &\vdash X \text{ set}
    \\ x \in X, y \in X                      &\vdash x \apart y \text{ prop}
    \\ x \in X, x \apart x                   &\vdash \bot
    \\ x \in X, y \in X                      &\vdash x \apart y \lor x = y
    \\ n \in \mathbb{N}, x_1 \dots x_n \in X &\vdash \exists y \in X, y \apart x_1 \land \dots \land y \apart x_n
\end{align*}$$

Everything on the left of the $\vdash$ is the assumptions. Everything on the right is the thing being claimed to exist.

As I mentioned earlier, **every geometric theory defines a topos.** This particular theory defines a topos known as the Schanuel topos.

## TODO

TODO: When going into more detail, focus on the big Zariski topos. That way, I can connect back to the Kock-Lavwere axiom in the intro.
