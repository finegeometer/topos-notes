# Quantum Mechanics via Noncommutative SDG

Work in the classifying topos of local star-rings. *Not* necessarily commutative ones.

Let $C$ be the universal local star-ring. By theorem 4.11 of [this paper](https://rawgit.com/iblech/internal-methods/master/paper-qcoh.pdf),
we have $A \cong ((A \xrightarrow{C-alg} C) \to C)$, where $A$ is any finitely-presented $C$-algebra.
In the forwards direction, the isomorphism maps $a$ to $f \mapsto f(a)$.

Following the referenced paper, I call this theorem *quasicoherence*.

## Basics

Let's examine some important objects in the topos.

First, there's $C$ itself. Quasicoherence shows that every function $C \to C$ is a polynomial in $x$ and $x^*$.
I mean polynomials in the maximally general sense; coefficients are *interleaved* with the indeterminates.

But what if we want more normal polynomials, where the coefficients commute with the indeterminates?
Well, homomorphisms $C[x,x^*] \to C$ correspond to elements $x \in C$ which commute with every element of $C$.
In other words, to elements of the *center* $Z(C)$. So quasicoherence says maps $Z(C) \to C$ are traditional polynomials.
(I'm assuming the finite presentability condition without checking it.)

---

Next, let's consider $R = \{x \in C | x^* = x\}$, and $I = \{x \in C | x^* = -x\}$.
Assuming the existence of $\frac{1}{2} \in C$, we can define the real and imaginary parts,
$\Re : C \to R$ and $\Im : C \to I$, as $\Re(x) = \frac{x + x^*}{2}$ and $\Im(x) = \frac{x - x^*}{2}$.
This exhibits $C$ as a product $R \times I$.
If we further assume the existence of $i \in C$, we have $R \cong I$, so $C \cong R^2$.

It's interesting that this is $R \times I$, and not $\{(x,y) \in R \times I \mid [x,y] = 0\}$.
The real and imaginary parts of a complex number *don't have to commute with each other!*

A bit more thought shows $[\Re(x),\Im(x)] = [\frac{x + x^*}{2}, \frac{x - x^*}{2}] = \frac{[x,x] - [x,x^*] + [x^*,x] - [x^*,x^*]}{4} = \frac{[x^*,x]}{2}$.
So the noncommutativity of the real and imaginary parts is captured by the value of $[x^*,x] \in R$.
And this is better, because $[x^*,x]$ is well-defined even when $C$ has characteristic 2.

(This does mean we don't have $x^*x = xx^*$ in general. So we define $\lVert x \rVert^2 = \frac{x^*x + xx^*}{2}$.)

Functions $R \to C$ are polynomials. Functions $R \to R$ are polynomials with real coefficients.
Functions $C \to R$ are a bit more subtle: they're polynomials in $x$ and $x^*$,
where the coefficient of e.g. $x^*xx$ is conjugate to the coefficient of $x^*x^*x$.
And as before, mapping out of $Z(R)$ or $Z(C)$ allows the coefficients of the polynomial to commute with the indeterminates.

## Calculus

Next, let's consider infinitesimals.

Let $\Delta = \{x \in Z(R) \mid x^2 = 0\}$.
Quasicoherence shows that functions $\Delta \to C$ correspond to elements of $C[\epsilon]/(\epsilon^2 = 0, \epsilon = \epsilon^*)$.
In other words, every function $\Delta \to C$ is uniquely of the form $\epsilon \mapsto a + b\epsilon$.

So we can define the derivative of a function $f : Z(R) \to C$ at $t$ to be the unique value $f'(t)$ such that $f(t+\epsilon) = f(t) + \epsilon f'(t)$ for all $\epsilon \in \Delta$.

---

Similarly, we can consider the set $i\Delta = \{x \in Z(I) \mid x^2 = 0\}$.
Again, every function $i\Delta \to C$ is uniquely of the form $\epsilon \mapsto a + b\epsilon$.
This allows us to define the "imaginary derivative".

Functions $Z(R) \to R$ have derivative in $R$, and functions $Z(R) \to I$ have derivative in $I$.
But functions $Z(I) \to R$ have imaginary derivative in $i$, and functions $Z(I) \to I$ have imaginary derivative in $R$.

---

More generally, suppose we have a function $f : X \to Y$.
This lifts to a function $Df : (x : X) \to T_x X \to T_{f(x)} Y$, where $T_x X = \{f : \Delta \to X \mid f(0) = x\}$ is the tangent space at $x$.

This works no matter *what* kind of types $X$ and $Y$ are! You just have to be careful about their tangent spaces.
Common types like $C$, $R$, $I$, $Z(C)$, et cetera are their own tangent spaces, but types like $R^+$ might be weirder.


<!-- If we want to take derivatives of functions $Z(C) \to C$, we need to specify the direction of the derivative. -->

## Positivity

TODO

## Distributions

Define $\mathcal{D}(X) = ((X \to C) \xrightarrow{C-linear} C)$.

TODO: Left or right linearity? Or do I need to fix this some other way?

We can lift functions to act on distributions:
$$\begin{align*}
    \mathrm{map} &: (X \to Y) \to (\mathcal{D}^+(X) \to \mathcal{D}^+(Y))
    \\ \mathrm{map}&(f)(d)(\phi) = d(\phi \circ f)
\end{align*}$$

We can also lift differential equations to distributions.
Suppose we have the following setup:
$$\begin{align*}
    v &: (x : X) \to T_x X
    \\ f &: Z(R) \to X
    \\ f'&(t) = v(f(t))
\end{align*}$$
And assume $X$ is sufficiently nice. (TODDO: How nice? Vector space? Affine space? Microlinear space? Any space?)

We can rephrase the differential equation as follows.
$$\forall \epsilon \in \Delta, f(t + \epsilon) = f(t) + \epsilon v(f(t))$$
$$\forall \epsilon \in \Delta, f(t + \epsilon) = (x \mapsto x + \epsilon v(x)) (f(t))$$

Now we lift to distributions. We replace $f : Z(R) \to X$ with $f : Z(R) \to \mathcal{D}^+X$.
$$\forall \epsilon \in \Delta, f(t + \epsilon) = \mathrm{map} (x \mapsto x + \epsilon v(x)) (f(t))$$

And we rephrase.
$$\begin{align*}
    f(t + \epsilon)(\phi) &= \mathrm{map} (x \mapsto x + \epsilon v(x)) (f(t)) (\phi)
    \\ &= f(t)(\phi \circ (x \mapsto x + \epsilon v(x)))
    \\ &= f(t)(x \mapsto \phi(x + \epsilon v(x)))
    \\ &= f(t)(x \mapsto \phi(x) + \epsilon D\phi(x)(v(x)))
    \\ &= f(t)(\phi) + \epsilon f(t)(x \mapsto D\phi(x)(v(x)))
\end{align*}$$

So:
$$f'(t)(\phi) = f(t)(x \mapsto D\phi(x)(v(x)))$$

If we worked with imaginary derivatives and $i\Delta$ instead, we would have exactly the same derivation and result.

### Example

What is a circularly symmetric distribution on $C$?

Set up a differential equation describing rotation.
$$\begin{align*}
    f &: Z(I) \to C
    \\ f'&(t) = f(t)
\end{align*}$$

For this section, all derivatives with refer to *imaginary derivatives*, meaning we use $i\Delta$ instead of $\Delta$.

The distribution equivalent is as follows:
$$\begin{align*}
    f &: Z(I) \to \mathcal{D}^+(C)
    \\ f'&(t)(\phi) = f(t)(x \mapsto D\phi(x)(x))
\end{align*}$$

We want the distribution to stay static under rotation.
$$\begin{align*}
    f &: \mathcal{D}^+(C)
    \\ 0 &= f(x \mapsto D\phi(x)(x))
\end{align*}$$

The expression $D\phi(x)(x)$ implicitly uses the equivalence $T_x C \cong C$.
Written out properly, we really want the unique $b$ such that $D\phi(x)(\delta \mapsto x + x\delta)(\epsilon) = D\phi(x)(\delta \mapsto x + x\delta)(0) + b\epsilon$.
Simplifying:
$$\begin{align*}
    b\epsilon &= D\phi(x)(\delta \mapsto x + x\delta)(\epsilon) - D\phi(x)(\delta \mapsto x + x\delta)(0)
    \\ &= \phi(x + x\epsilon) - \phi(x + x0)
    \\ &= \phi((1+\epsilon)x) - \phi(x)
\end{align*}$$

Now, $\phi : C \to C$, so it is a polynomial in $x$ and $x^*$. By linearity, it suffices to handle all monomials.
And if $\phi$ is a monomial containing $m$ copies of $x$ and $n$ copies of $x^*$, in any order,
then $\phi((1+\epsilon)x) - \phi(x) = (m-n)\epsilon \phi(x)$. So $D\phi(x)(x) = (m-n) \phi(x)$.

Therefore, the requirement $0 = f(x \mapsto D\phi(x)(x))$ forces $f$ to return zero when given any monomial with a different number of $x$s and $x^*$s.

In conclusion, a circularly-symmetric distribution is one that only depends on the coefficients of those terms
that have an equal number of $x$s and $x^*$s.

## Harmonic Oscillator

Let us turn our attention to the harmonic oscillator.

This system is normally described by the differential equations $\dot{x} = p$ and $\dot{p} = -x$.
But by taking $x$ and $p$ to be the real and imaginary parts of a complex number, this becomes the system $\dot{x} = -ix$.

To remove the dependence on $i$, we can make time imaginary.

$$\begin{align*}
    f &: Z(I) \to C
    \\ \dot{f}&(t) = f(t)
\end{align*}$$

This is exactly the differential equation from before.
So the static distributional solutions are the rotationally symmetric ones;
those which only depend on terms with an equal number of $x$s and $x^*$s.

### Classical

For the classical harmonic oscillator, we restrict the phase space from $C$ to $\{x \in C | [x,x^*] = 0\}$.
At the level of distributions, this means the distribution should return the same output for e.g. $xx^*$ and $x^*x$.

So(see TODO section) a static distributional solution is defined by its action on each $\lVert x \rVert^{2n}$, or equivalently by its action on $(x^*)^n x^n$.

If we want a *probability distribution*, we further want $d(1) = 1$ and $d(P^*P) \geq 0$ for all $P$.

The expected energy in the harmonic oscillator is $d(\lVert x \rVert^2)$.
The lowest this can be is zero, and this is achieved by the distribution $d(\phi) = \phi(0)$.

If we want to force the energy to be *exactly* $E$, rather than just expected, we should set $\mathrm{map}(\lVert-\rVert^2)(d)(\phi) = \phi(E)$.
Simplifying, $d(\phi \circ \lVert-\rVert^2) = \phi(E)$. So $d$ is the distribution $\lVert x \rVert^{2n} \mapsto E^n$.

This is a probability distribution whenever $E \geq 0$. So the system has continuous energy levels.

### Quantum

Now for the quantum case. Instead of restricting the phase space to $\{x \in C | [x,x^*] = 0\}$, we restrict it to $\{x \in C | [x,x^*] = 1\}$.

Again, a static distributional solution is defined by its action on each $\lVert x \rVert^{2n}$, or alternatively by its action on $(x^*)^n x^n$.
And again, the expected energy in the harmonic oscillator is $d(\lVert x \rVert^2)$.
But this time, the expected energy cannot be zero, because we have $d(\lVert x \rVert^2) = d(x^*x + \frac{1}{2}) = d(x^*x) + \frac{1}{2} \geq \frac{1}{2}$.

If we want to force the energy to be *exactly* $E$, rather than just expected, we should set $d(\phi \circ \lVert-\rVert^2) = \phi(E)$.
So $d$ is the distribution $\lVert x \rVert^{2n} \mapsto E^n$.

When is this a probability distribution? Let's do some computations.
$$\begin{align*}
    (x^*)^{n+1}x^{n+1} &= \lVert x \rVert^2 (x^*)^nx^n - (n+\tfrac{1}{2})(x^*)^nx^n
    \\ &= (\lVert x \rVert^2-n-\tfrac{1}{2})(x^*)^nx^n
    \\ (x^*)^n x^n &= \prod_{k = \tfrac{1}{2}}^{n-\tfrac{1}{2}} (\lVert x \rVert^2-k)
    \\ d((x^*)^n x^n) &= \prod_{k = \tfrac{1}{2}}^{n-\tfrac{1}{2}} (E-k)
\end{align*}$$

So $\prod\limits_{k = \tfrac{1}{2}}^{n-\tfrac{1}{2}} (E-k)$ had better be positive for all $n$.
Speaking in terms of ordinary real numbers, the only energies that work are $\frac{1}{2}, \frac{3}{2}, \frac{5}{2}, \dots$.
So the system has evenly-spaced discrete energy levels.

### Vacuum State

The lowest possible energy was $E = \frac{1}{2}$. And the analysis above shows this state is achieved by
$\mathrm{vacuum}((x^*)^n x^n) = \prod\limits_{k = \tfrac{1}{2}}^{n-\tfrac{1}{2}} (\tfrac{1}{2}-k) = \begin{cases} 1 & n = 0 \\ 0 & \text{else}\end{cases}$.
This is the vacuum state.

Let us compute the position-space distribution corresponding to the vacuum state.
$$\begin{align*}
    \mathrm{map}(\Re)(\mathrm{vacuum})(x^n) &= \mathrm{vacuum}(x \mapsto (\Re(x))^n)
    \\ &= \mathrm{vacuum}(x \mapsto (\tfrac{x + x^*}{2})^n)
    \\ &= 2^{-n} \mathrm{vacuum}(x \mapsto (x + x^*)^n)
\end{align*}$$

$\mathrm{vacuum}$ reexpresses the polynomial so that the $x^*$s precede the $xs$, then picks out the constant term.
A counting argument shows that this process, when applied to a monomial,
counts the *number of ways* to match up the $x$s with the $x^*$s, with each $x$ preceding its corresponding $x^*$.
So $\mathrm{vacuum}(x \mapsto (x + x^*)^n)$ is the number of ways to pair up $n$ objects, which is $\begin{cases} (n-1)!! & n \text{ even} \\ 0 & n \text{ odd}\end{cases}$.

So the position-space distribution is $x^n \mapsto \begin{cases} \frac{1}{2} \frac{3}{2} \frac{5}{2} \dots \frac{n-1}{2} & n \text{ even} \\ 0 & n \text{ odd}\end{cases}$.
Since this equals $\int_{-\infty}^\infty x^n \frac{e^{-x^2}}{\sqrt\pi}$, we conclude that the amplitude of the position-space wavefunction
is a Gaussian, given by $\frac{e^{-x^2}}{\sqrt\pi}$.

# TODO

- My use of Z is still broken. In particular, $x \in Z(C)$ implies $[x,x^*] = 0$, but I act like it doesn't.
- There should be a monoidal closed product. How do I work with it, and how do derivatives interact with it?
- Actually, the previous two items are probably the same question.









