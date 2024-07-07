# Designing a Topos-Theoretic Proof Assistant

I would like to see a proof assistant that builds in the ideas of topos theory.
So if you want to prove something about calculus, you can work in a smooth topos, and translate the result back to the topos of sets.

## Existing Work

- [Agda's flat modality](https://agda.readthedocs.io/en/latest/language/flat.html) allows working with two toposes.
- [Multimode Type Theory](https://anuyts.github.io/files/mtt-paper.pdf) allows working with a collection of toposes with *essential* geometric morphisms between them.
    - [A followup paper](https://arxiv.org/abs/2303.02572) relaxes this to arbitrary geometric morphisms, as long as the "mode theory" is finite.

## My Complaints

I find the state of the art unsatisfactory, for the following reasons.
- **Generality:**

    I want the *user* to define the toposes they work in, not the language implementer.
- **Complexity:**
    
    The point of modalities is to move along a geometric morphism from another topos.
    The point of lambda abstraction is to move along a geometric morphism from a slice topos.
    So lambda abstraction should be a special case of the modal operations.

    But for whatever reason, existing approaches treat lambdas and modalities with entirely separate language constructs.

    It's even possible that universe levels should be a special case of modes.
    But there aren't geometric morphisms between different universe levels; just flat functors.

## My Ideas

I have tried for a while to design a good solution. Nothing's quite worked, but I believe my ideas are on the right track.

### Reinterpreting Lambda Calculus

Ordinary dependent lambda calculus already supports a certain class of toposes. Slice toposes!
Can we generalize this to all toposes?

The interpretation would be as follows:
- If $\Gamma$ is a context, then $\interp{\Gamma}$ is a topos.
    - The empty context interprets as $\Set$.
    - $\interp{\Gamma, A} = \interp{\Gamma}_{/\interp{A}}$.
- If $\Gamma \vdash A \text{ type}$, then $\interp{A}$ is an object of $\interp{\Gamma}$.
- If $\Gamma \vdash a : A$, then $\interp{a}$ is a global element of $\interp{A}$.
- If $\Gamma \vdash \sigma : \Delta$, then $\interp{\sigma}$ is a geometric morphism from $\interp{\Gamma}$ to $\interp{\Delta}$.

This *almost* works. The only things that go wrong are the rules commuting substitutions past $\Pi$-types, lambdas, and applications.

So weaken the lambda calculus by removing these rules!
Then to compensate for the fact that a substitution can get "stuck" between a lambda and an application, generalize the $\beta$-rule as follows.
$$(\lambda e_1)[\sigma]e_2 \equiv e_1[\sigma, e_2]$$

With this modified calculus, the interpretation works perfectly.
So, in theory, this calculus could be used as a foundation on which to build a topos-theoretic language.
However, it is unclear how to extend it to fully support topos-theoretic reasoning.

Also, this approach produces explicit substitutions in the syntax, which I see as ugly.

### Toposes as Meta-contexts

If we are to work with arbitrary toposes, we need some way to specify them.
There are two main options:
- Sheaf Toposes
- Classifying Toposes

I'm inclined toward the latter.

To specify a classifying topos, we need to state a geometric theory.
Traditionally, this means defining the sorts, functions, relations, and axioms.
But we simplify as follows:
- We can generalize to allow functions, etc. to refer to any geometric type, not just the raw sorts.
    - In fact, any type is expressible as a geometric type, using trickery with large colimits. They just might not transform as you'd expect under geometric transformations.
- We can allow sorts to be parameterized: $x : A \vdash B \text{ type}$. This is encoded as a sort $\Sigma B$ and a function $\Sigma B \to A$.
- Now relations are redundant. Whenever you have $P \text{ prop}$, replace it with $P \text{ type}$ and $x, y : P \vdash x = y$.
- And axioms are redundant — they're just functions into equality types.

So a theory is a list of statements of the form $x_1 : X_1, \dots, x_n : X_n \vdash Y \text{ type}$ and $x_1 : X_1, \dots, x_n : X_n \vdash y : Y$.

This is reminiscent of contexts in type theory. For contexts, we have these rules.
<!-- Hacky workaround for the lack of \inferrule -->
$$\begin{gather*}
    \\ \hline \epsilon \text{ ctx}
\end{gather*} \qquad\qquad \begin{gather*}
    \Gamma \vdash A \text{ type}
    \\ \hline \Gamma, A \text{ ctx}
\end{gather*}$$

And for theories/toposes/modes, we have these.
$$\begin{gather*}
    \\ \hline \epsilon \text{ mode}
\end{gather*} \qquad\qquad \begin{gather*}
    m \text{ mode}
    \\ \hline m, (\Gamma \Rightarrow \Type) \text{ mode}
\end{gather*} \qquad\qquad \begin{gather*}
    m \vdash (\Gamma \vdash A \text{ type})
    \\ \hline m, (\Gamma \Rightarrow A) \text{ mode}
\end{gather*}$$

It seems that modes are "meta-contexts".
Just as types are defined in contexts, contexts are defined in modes.
And just as we have substitutions to move between contexts, we have contexts to move between modes.
We even have an equivalent of variables — the generic model!

**Problems with this idea:**
- What if the theory has an infinite number of sequents?
- How do I make modalities depend on values?

## Other Issues

- How should the language handle monoial toposes?
- How should it handle the following reasoning principle?
    "Since the category of manifolds embeds into the Dubuc topos, it suffices to prove the relevant map exists there."
