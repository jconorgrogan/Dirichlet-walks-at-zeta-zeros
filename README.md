# Dirichlet Walk: A Visual-of-5000-Riemann-zeta-zeros-alternating--series-on-complex-plane

A (to my knowledge) unique/novel way of visualizing the zeta zeros  

<img width="480" height="954" alt="image" src="https://github.com/user-attachments/assets/f6268d77-71cf-4509-8c1d-f512be9cdeae" />

<img width="697" height="683" alt="image" src="https://github.com/user-attachments/assets/8c671482-fbfd-49a8-9c8a-062e60ff855d" />

This project visualizes the complex-plane trajectories of partial sums evaluated at nontrivial Riemann zeta zeros.

For each zero \( \rho_k = \tfrac{1}{2} + i t_k \) and mode parameter \( p \), we compute:

\[
S_N(t_k, p) = \sum_{n=1}^{N} M_p(n) \cdot n^{-1/2} \cdot e^{-i t_k \log n}
\]

where the multiplier is:

\[
M_p(n) =
\begin{cases}
1 - p, & \text{if } p \mid n \\
1, & \text{otherwise.}
\end{cases}
\]

---
---

## Here's what we did and what we asked:

1. **Take a list of nontrivial Riemann zeros**

\[
\rho_k = \tfrac{1}{2} + i\,t_k, \quad k = 1, 2, \dots, K,
\]

where each \( t_k \) is the imaginary ordinate of a zeta zero  
(e.g., \( t_1 = 14.1347, \; t_2 = 21.0220, \dots \)).

---

2. **For each zero, define the truncated series**

The base Dirichlet-type sum on the critical line is

\[
S_N(t_k, p) = \sum_{n=1}^{N} M_p(n)\,n^{-1/2}\,e^{-i\,t_k \log n},
\]

where \( M_p(n) \) is a mode-dependent multiplier determined by the chosen
`seriesType` value \( p \):

\[
M_p(n) =
\begin{cases}
1, & p = 1,\\[4pt]
(1 - p), & n \equiv 0 \pmod p, \; p > 1,\\[4pt]
1, & \text{otherwise.}
\end{cases}
\]

---

**Code equivalent:**
```js
if (p > 1) {
  const multiplier = (n % p === 0) ? (1 - p) : 1;
  re *= multiplier;
  im *= multiplier;
}
```

---

3. **Compute the trajectory**

Iteratively update:

\[
S_0 = 0, \quad
S_n = S_{n-1} + M_p(n)\, n^{-1/2} e^{-i t_k \log n}.
\]

**Code:**
```js
z += Math.pow(n, -0.5) * M_p(n) * Math.exp(-i * t_k * Math.log(n));
points.push([Re(z), Im(z)]);
```

Each term is a complex vector of length \( 1 / n^{1/2} \),
rotated by angle \( t_k \log n \) and optionally phase-flipped or rescaled by \( M_p(n) \).

---

4. **Compute and visualize the walk**

By the end of the loop, the script has all points
\[
(x_n, y_n) = (\Re S_n, \Im S_n)
\]
for each zero \( t_k \) and mode \( p \).

These points trace a **zeta spiral** — a quasi-random walk whose step length decreases as \( 1 / n^{1/2} \).

---

5. **Analyze spatial and radial densities**

The program then visualizes and measures:

- \( H(x,y) \): a 2-D heat map showing where the walk spends time (brightness ∝ density).  
- \( D(r) \): a 1-D radial density showing how often the walk crosses each radius \( r = |S_n| \).

---

### Question

Given this definition of \( S_N(t_k, p) \) and the corresponding trajectories in the complex plane,  
should we expect any particular **geometric or statistical structure**  
(e.g., recurring radii, phase locking, or clustering)  
to emerge as \( N \to \infty \) or as \( p \) varies?

### What we found  √p rings (p-adic self-similarity)

Fix a zero s = 1/2 + i t_k and integer p ≥ 2. With coefficients a_n = 1 − p·1_{p|n},
the partial sums satisfy the two-scale identity
S_N(s,p) = T(N) − p^{1−s} T(⌊N/p⌋),  T(x)=∑_{n≤x} n^{-s}.

Define W_N := N^{1/2} e^{i t_k log N} S_N(s,p). Then, keeping the discrete
boundary term, one obtains the coarse recursion
W_{pM} = W_M − (p−1)/2 + O(M^{-1}).

Consequences:
- self-similarity under N ↦ pN with scale p^{-1/2} and rotation −t_k log p,
- log-periodic build-up in the radial density at radii forming a geometric ladder
  r_m ∝ (√p)^m   (so consecutive rings obey r_{m+1}/r_m = √p).
Stacking many zeros randomizes phase and leaves circular annuli at those radii.
For p=2 (alternating case) the dominant ring is at r ≈ √2.
