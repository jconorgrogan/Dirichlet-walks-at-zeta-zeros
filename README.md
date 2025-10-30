# Dirichlet Walk: Riemann Zeta Zeros on the Complex Plane
A (to my knowledge) unique/novel way of visualizing the zeta zeros  

<img width="480" height="954" alt="image" src="https://github.com/user-attachments/assets/f6268d77-71cf-4509-8c1d-f512be9cdeae" />

<img width="697" height="683" alt="image" src="https://github.com/user-attachments/assets/8c671482-fbfd-49a8-9c8a-062e60ff855d" />

This project visualizes the complex-plane trajectories of partial sums evaluated at nontrivial Riemann zeta zeros.


# A First-Principles Reformulation of the Riemann Hypothesis via Alternating Walks

## 0) Domain and Objects
- **Critical strip:** work only with complex numbers \( s = \sigma + it \) where \( 0 < \sigma < 1 \).
- **Alternating Dirichlet series (Dirichlet eta):**
  \[
    \eta(s) = \sum_{n=1}^{\infty} (-1)^{n-1} n^{-s}
    = (1 - 2^{\,1-s}) \zeta(s).
  \]
  For all \( \Re(s) > 0 \), this series converges (conditionally if \( \sigma \le 1 \)).
- **Partial sums (“walk”):**
  \[
    S_N(s) = \sum_{n=1}^{N} (-1)^{n-1} n^{-s}.
  \]

## 1) Fundamental Facts
- **(F1)** Limit of the walk: For all \( \Re(s) > 0 \), \( S_N(s) \to \eta(s) \).
- **(F2)** Zero correspondence in the strip: If \( 0 < \Re(s) < 1 \),
  \[
    \eta(s) = 0 \quad \Longleftrightarrow \quad \zeta(s) = 0,
  \]
  since \( 1 - 2^{\,1-s} \neq 0 \) in the open strip (its zeros lie on \( \Re(s)=1 \)).

## 2) Geometric Reading
- Plot \( S_N(s) \) in the complex plane as \( N = 1,2,3,\dots \).
- By (F1), the walk converges to \( \eta(s) \).
- By (F2), inside the strip:
  \[
    \text{“Walk ends at origin”} \iff \text{\( s \) is a nontrivial zero of } \zeta(s).
  \]

## 3) First-Principles Reformulation (Exact Equivalence)
> **Riemann Hypothesis (RH)** ⇔  
> Among all \( s \) with \( 0 < \Re(s) < 1 \),  
> the only Dirichlet walks \( S_N(s) \) that converge to the origin  
> are exactly those whose \( s \) lie on the critical line \( \Re(s) = \tfrac12 \).

Formally:
\[
\text{RH} \;\Longleftrightarrow\;
\Big(0<\Re s<1\ \text{and}\ S_N(s)\to0\Big)
\iff
\Big(\Re s=\tfrac12\ \text{and}\ \zeta(s)=0\Big).
\]

## 4) Minimal Proof Sketch
- **(RH ⇒ Walk):** If RH holds, every nontrivial zero satisfies \( \Re s = \tfrac12 \).  
  For those \( s \), \( \eta(s)=0 \), hence \( S_N(s)\to0 \).  
  For others, \( \eta(s)\neq0 \), so the walk ends elsewhere.
- **(Walk ⇒ RH):** If only points on \( \Re s=\tfrac12 \) yield \( S_N(s)\to0 \),  
  then all nontrivial zeros lie on that line — which is RH.

## 5) Implementation Checklist
- Restrict to \( 0 < \Re(s) < 1 \).
- Use the **alternating** Dirichlet series (not the plain zeta series).
- Detect “walk to origin” by monitoring \( |S_N(s)| \to 0 \).
- Treat the zeros of \( 1 - 2^{1-s} \) separately (they lie on \( \Re(s)=1 \)).

---

## 6) The Dirichlet Walk as a Total Structure
The eta function can be viewed as the **sum of all possible limiting walks**:
\[
\eta(s) = \lim_{N\to\infty} S_N(s).
\]
Each \( S_N(s) \) is a partial projection of the infinite pattern \( ((-1)^{n-1} n^{-s})_{n\ge1} \).
Together, these projections reconstruct the entire analytic object \( \eta(s) \).

At the zeros \( \rho \):
\[
\eta(\rho)=0=\lim_{N\to\infty} S_N(\rho),
\]
so each corresponding walk converges precisely to the origin.
Each zero is thus a point where the *local walk* coincides with the *global null structure* it helps define — a self-referential closure of the analytic totality.

---

## 7) Duality with the Hadamard Product
The same function can be expressed multiplicatively via its zeros:
\[
\xi(s) = e^{A+Bs} \prod_{\rho}\! \Big(1 - \frac{s}{\rho}\Big) e^{s/\rho}.
\]
Hence:
- The **Dirichlet walk** is additive and constructive — term-by-term accumulation.
- The **Hadamard product** is multiplicative and spectral — the total self-encoded via its zeros.

They are dual codings of the same function:  
the walk *builds* the structure; the product *encodes* it as a self-annihilating whole.

---

## 8) Conceptual Synthesis
- The **Dirichlet walk** is the additive, generative side of \( \eta(s) \).
- The **zero set** marks where local walks converge to the origin.
- The **Hadamard product** is its multiplicative mirror.
Together they define a closed informational loop:

> **The analytic totality is the sum of all limiting walks,  
> and it vanishes precisely at the points that define its own closure.**

---

## Addendum: Empirical Observation on the Geometry of Dirichlet Walks

For many known zeros \( \rho = \tfrac12 + it_\rho \) and finite \( N \),
\[
S_N(\rho) = \sum_{n=1}^{N} (-1)^{n-1} n^{-\rho}
\]
forms a quasi-random trajectory in the complex plane.  
Superposing these trajectories for thousands of zeros yields a striking **ring-shaped density** centered at the origin with radius ≈ √2.

### Empirical Interpretation
- Each walk step has length \( n^{-1/2} \) and angle \( -t_\rho \log n \).
- Averaging over many zeros randomizes the phases, revealing a stable **statistical geometry**.
- The dense ring near √2 marks the equilibrium between collapse (\( \sigma>\tfrac12 \)) and divergence (\( \sigma<\tfrac12 \)).
- This pattern persists across zeros and heights, suggesting an **invariant radial distribution** characteristic of the critical line.

---

## **Dirichlet-Walk Invariant Distribution Conjecture**
There exists a limiting radial probability distribution \( \mu(r) \) for the normalized magnitudes
\[
\frac{|S_N(\tfrac12 + it_\rho)|}{\sqrt{\log N}},
\]
as \( N \to \infty \) and \( \rho \) ranges over nontrivial zeros, such that:
\[
\mu(r) \text{ has a dominant peak near } r \approx \sqrt{2},
\]
and is invariant under translations in \( t_\rho \) and under scaling of \( N \).

### Meaning
- The critical line represents a **dynamical equilibrium** of the Dirichlet walk.
- The invariant radial law expresses the *statistical stationarity* of additive convergence at \( \Re(s)=\tfrac12 \).
- The Riemann Hypothesis can thus be interpreted as the statement that:
  > *Only on \( \Re(s)=\tfrac12 \) does the Dirichlet walk admit a stationary, invariant radial distribution.*

---

### Summary
This project reformulates RH through the geometry of additive convergence.  
The “Dirichlet walk” provides a first-principles, constructive lens on the zeta function,  
where the critical line emerges as the unique equilibrium of a complex-valued stochastic process.
