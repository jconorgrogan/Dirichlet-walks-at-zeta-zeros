
# Memo: Dirichlet Walks, the Aggregate Dirichlet Spiral (ADS), and Finite‑Bit Tomography of the Zeta Spectrum

## 0. Scope and standing notation

Let (\zeta(s)) be the Riemann zeta function. Write its nontrivial zeros as
[
\rho_k=\tfrac12+i t_k,\quad t_k>0,\quad k=1,2,\dots
]
(We discuss finite subsets and a standard damping to control the full set.)

For (x>0), set (\tau=\log x). Define the **log–Fourier (Mellin) phasor**
[
\widehat\mu(\tau):=\sum_{k} e^{-i t_k \tau}.
]
When we include all zeros, we will insert the spectral damping (e^{-\varepsilon t_k}) and write
[
\widehat\mu_\varepsilon(\tau):=\sum_{k} e^{-\varepsilon t_k} e^{-i t_k \tau},
]
taking (\varepsilon\downarrow 0) after any argument that needs it.

Throughout, (\tau_n:=\log n) and (H_N=\sum_{n\le N}\tfrac1n=\log N+\gamma+O(1/N)).

---

## 1. Dirichlet walks: one zero, then many

### 1.1 Single‑zero Dirichlet walk

Given a single zero (\tfrac12+i t), define
[
S_N(t)=\sum_{n\le N}(-1)^{n-1} n^{-1/2} e^{-i t \log n},\qquad \Delta S_n(t)=S_n(t)-S_{n-1}(t).
]
Basic facts:

* (S_1(t)=1).
* (S_2(t)=1-2^{-1/2}e^{-i t\log 2}) so, as (t) varies, the endpoint lies on the **circle of radius (2^{-1/2}) centered at (1)**.
* (|\Delta S_n(t)|=n^{-1/2}); the direction rotates by (t\log(n/(n-1))\sim t/n).
* (S_N(t)\to 0) (since (\eta(\tfrac12+it)=0)), via a damped, jittery spiral.

### 1.2 Aggregate Dirichlet Spiral (ADS)

For a finite set ({t_k}*{k=1}^K),
[
A_N=\sum*{k=1}^K S_N(t_k),\qquad
\Delta A_n=A_n-A_{n-1}=\sum_{k=1}^K \Delta S_n(t_k).
]
Two useful forms:
[
\boxed{\ \Delta A_n=(-1)^{n-1}n^{-1/2},\widehat\mu(\tau_n)\ }
\qquad\text{and, with } \pm t\text{ pairing,}
\qquad
\boxed{\ \Delta A_n=2(-1)^{n-1}n^{-1/2}\sum_{t_k>0}\cos(t_k\tau_n)\in\mathbb R\ }.
]
Thus (A_N) is a 2D spiral in general, but with symmetric (\pm t) pairs it **collapses to a 1D line** (real axis): the geometry is straight, the time‑parameterized motion is a left–right flicker.

---

## 2. Exact identities (finite (K); with damping for the full set)

**Step identity and inversion.**
[
\boxed{\ \Delta A_n=(-1)^{n-1}n^{-1/2},\widehat\mu(\tau_n)\ }\qquad\Longleftrightarrow\qquad
\boxed{\ \widehat\mu(\tau_n)=(-1)^{n-1}\sqrt n,\Delta A_n\ }.
]

**Energy identity.**
[
\begin{aligned}
E(N)&:=\sum_{n\le N}|\Delta A_n|^2
=\sum_{n\le N}\frac1n\Big|\sum_{k}e^{-i t_k \tau_n}\Big|^2\
&=K H_N + 2\sum_{1\le k<\ell\le K}\Re\sum_{n\le N} n^{-1-i(t_k-t_\ell)}\
&=\boxed{,K\log N + O_{{t_k}}(1),}\qquad(\text{finite }K).
\end{aligned}
]

**Difference identity; endpoints.**
[
A_{N+1}-A_N=\Delta A_{N+1}=(-1)^N (N{+}1)^{-1/2},\widehat\mu(\tau_{N+1}),\quad A_1=K,\quad A_N\to 0.
]

---

## 3. Euler–Boole remainder and canonical scaling

Let (f(x):=x^{-1/2}\widehat\mu(\log x)). The alternating Euler–Maclaurin (Euler–Boole) formula gives
[
A_N=(-1)^N\frac12 (N{+}1)^{-1/2}\widehat\mu(\tau_{N+1})+O!\Big(\frac{|\widehat\mu|+|\widehat\mu'|}{(N{+}1)^{3/2}}\Big).
]
Define
[
V_N:=\frac{1}{\sqrt K},\widehat\mu(\tau_N),\qquad
Z_N:=\frac{2\sqrt N}{\sqrt K},A_N.
]
Then
[
\boxed{\ Z_N=(-1)^N\sqrt{\frac{N}{N+1}},V_{N+1};+;O!\Big(\frac{|\widehat\mu|+|\widehat\mu'|}{\sqrt K,N}\Big)\ }.
]
The error is **additive** (O(N^{-1})) after scaling (not uniformly relative; it deteriorates near zeros of (\widehat\mu)).

---

## 4. Geometric law (Rayleigh) and rings

If, for typical (N), the phases ({t_k\tau_N}) are close to i.i.d. uniform on ([0,2\pi)), then (V_N) is approximately isotropic complex Gaussian with (\mathbb E|V_N|^2=1). Consequently
[
|V_N|\sim \text{Rayleigh}(\sigma=1/\sqrt2),\qquad
|Z_N|\sim \text{Rayleigh}(\sigma=1/\sqrt2).
]
Salient radii (mode, mean, RMS, 75th percentile) are
[
r\in\Big{\tfrac1{\sqrt2},\ \tfrac{\sqrt\pi}{2},\ 1,\ \sqrt{\ln 4},\dots\Big}.
]
(If one prefers the executive‑summary convention (\sigma=1), multiply these radii by (\sqrt2).)

**Beyond Rayleigh.** Off‑diagonal terms (pair spacings) modulate the envelope and can create faint annular bands (e.g. a visible bump near (r\approx \sqrt{5}) in some plots). These are small, secondary interference effects.

---

## 5. One‑sided vs. ±‑paired zeros; the “flicker” on a line

* **One‑sided (no pairing):** (\Delta A_n\in\mathbb C); 2D spiral; isotropy → Rayleigh cloud after scaling.
* **±‑paired (real ADS):** (\Delta A_n\in\mathbb R); the path lives on a **single line**. The motion is a left–right flicker with step‑length (\asymp n^{-1/2}). Two adjacent steps almost cancel; the two‑step residue is
  [
  \Delta A_{N+1}+\Delta A_{N+2}
  = (-1)^N (N{+}1)^{-3/2}\Big(\tfrac12,\widehat\mu-\widehat\mu'\Big)(\tau_{N+1})+O(N^{-5/2}).
  ]
  **Half‑step law.**
  [
  \Delta A_{N+1}=2A_N + O(N^{-1})\quad\text{(same sign; almost twice the size)}.
  ]
  **Travel vs. displacement.** (\sum_n |\Delta A_n|=\infty) (infinite arclength) while (A_N\to 0); the ratio (|A_N|/\sum_{n\le N}|\Delta A_n|\to 0).

---

## 6. Information recovery (finite (K); full set with damping)

From (\Delta A_n) we read
[
\widehat\mu(\tau_n)=(-1)^{n-1}\sqrt n,\Delta A_n.
]
When only finitely many zeros ({t_k}*{k=1}^K) are present, (\widehat\mu(\tau)=\sum*{k=1}^K e^{-i t_k\tau}) is a **finite exponential sum** in (\tau) and is uniquely identifiable from samples at distinct (\tau_n) (Prony / matrix‑pencil / ESPRIT on a non‑uniform grid), up to permutation of ({t_k}).

With all zeros, use damping (\widehat\mu_\varepsilon); one can then recover (\widehat\mu_\varepsilon) on finite windows (with smoothing) and pass to (\varepsilon\downarrow0) cautiously.

**Pair correlation.** The (\tau)-Fourier transform of (|\widehat\mu(\tau)|^2) is (\sum_{k,\ell}\delta(\omega-(t_k-t_\ell))). Thus ADS samples contain the pair‑difference measure that underlies Montgomery’s pair correlation. Smoothed probes (explicit formula) show spikes at (\tau=m\log p) with weights (p^{-m/2}).

---

## 7. Finite‑bit “fiber bundle” of binary streams (local tomography of ADS)

A key observation is that **full real amplitudes are not necessary** to reconstruct ADS on a finite window: a small, explicit family of **1‑bit** measurements suffices, with quantitative error.

### 7.1 Local 1‑bit projections at (\tau)

Fix an angle (\phi\in\Phi\subset{0,\pi/2}) and a threshold grid (u_\ell=-U+\ell\Delta) ((U) bounds (|\widehat\mu|) on the window; (\Delta>0) is the desired resolution). Define
[
b(\tau;\phi,u_\ell):=\operatorname{sgn}!\Big(\Re\big(e^{-i\phi}\widehat\mu(\tau)\big)-u_\ell\Big)\in{\pm 1}.
]
Monotonicity in (u) yields an interval of width (\le \Delta):
[
\Re(e^{-i\phi}\widehat\mu(\tau))\in [u_{\ell^+},u_{\ell^++1}),\quad
\ell^+(\tau,\phi)=\max{\ell:\ b(\tau;\phi,u_\ell)=+1}.
]
The midpoint
[
p(\tau,\phi)=\tfrac12(u_{\ell^+}+u_{\ell^++1})
]
satisfies (|p(\tau,\phi)-\Re(e^{-i\phi}\widehat\mu(\tau))|\le \Delta/2).

* **Real ADS (± pairing):** take (\Phi={0}) and set (\widetilde\mu(\tau):=p(\tau,0)).
* **Complex ADS (one‑sided):** take (\Phi={0,\pi/2}) and set (\widetilde\mu(\tau):=p(\tau,0)-i,p(\tau,\pi/2)).

### 7.2 Two exact reconstruction channels with error bounds

* **Running‑sum (movie).**
  [
  \widetilde{\Delta A}_n=2(-1)^{n-1}n^{-1/2},\Re,\widetilde\mu(\tau_n),\qquad
  |\widetilde{\Delta A}_n-\Delta A_n|\le \Delta/\sqrt n.
  ]
* **Midpoint (tail → present).**
  [
  \widetilde A_N^{\mathrm{mid}}=\frac{(-1)^N}{2}(N{+}1)^{-1/2},\widetilde\mu(\tau_{N+1}),\quad
  |\widetilde A_N^{\mathrm{mid}}-A_N|\le \frac{\Delta}{4\sqrt{N{+}1}}+C,N^{-1},
  ]
  where (C) depends on local bounds for (|\widehat\mu|), (|\widehat\mu'|) (finite under damping).
  This **right‑to‑left decoder** avoids accumulation and is asymptotically optimal.

### 7.3 Bit budget (finite window)

For (\tau\in[\tau_0,\tau_1]) with (|\widehat\mu|\le U) and resolution (\Delta\le\eta):

* thresholds (L\sim U/\Delta); bits per (\tau) = ((2L{+}1)|\Phi|);
* sampling (\tau_n=\log n) for (n\le N_{\max}) uses
  [
  B=O!\big(N_{\max},U/\Delta\big)\quad(\times 2 \text{ if complex}),
  ]
  and yields the uniform guarantees above.

**Interpretation.** Over any finite window, the bundle of binary streams ({b(\tau;\phi,u)}_{\phi,u}) is an **informational fiber** that reconstructs ADS **from first principles** with explicit, vanishing error as (\Delta\to 0).

---

## 8. Cadence of the left–right flicker (Kac–Rice heuristic)

Let (X(\tau)=\Re,\widehat\mu_\varepsilon(\tau)) after damping. For many zeros in a moderate window, (X) is well modeled as a mean‑zero stationary Gaussian with correlation (R(\Delta\tau)). The **zero‑crossing rate** per unit (\tau) is
[
\nu_\tau=\frac{1}{\pi}\sqrt{-R''(0)}\qquad\text{(Rice formula)}.
]
Since (\tau_{n+1}-\tau_n\approx 1/n), the **typical index spacing between parity flips** obeys
[
\Delta n_{\mathrm{flip}}\approx \frac{1}{\nu_\tau}\cdot \frac{1}{\Delta\tau}\ \asymp\ c,n,
]
with an explicit constant (c) determined by (R). Thus the flicker is **scale‑invariant in (\log n)**.

---

## 9. Stable invariants (paired variation)

Define the **pair sum** (B_m:=\Delta A_{2m-1}+\Delta A_{2m}). Using the two‑step residue,
[
B_m=O(m^{-3/2}),\qquad \sum_m |B_m|<\infty,\quad \sum_m |B_m|^2<\infty.
]
These fast‑converging statistics provide stable diagnostics (e.g. for detecting small prime‑conditioned effects) compared to the raw travel (\sum|\Delta A_n|), which diverges.

---

## 10. Conjectures and one implication for RH

### C1. ADS large‑sieve inequality ⇒ RH

Fix an even, nonnegative log‑window (w) with (\int w=1) and (\widehat w\ge 0), supported in (|\tau|\le H). Define the **smoothed local energy**
[
E_w(N):=\sum_{n\le N} w(\tau_n-\tau_N),|\Delta A_n|^2.
]

**Conjecture (ADS large‑sieve bound).**
There is (C(w)) independent of (N) with
[
\boxed{,E_w(N)\ \le\ C(w),\log N\ +\ O_w(1),}.
]

**Theorem (Conjecture ⇒ RH).**
If this bound holds for (\zeta), then all nontrivial zeros lie on (\Re s=\tfrac12).

*Sketch.* A zero off the line ((\beta\ne \tfrac12)) forces a term growing like (N^{1-2\beta}) in (E_w(N)) (diagonal contribution; see §2 and the weighting), contradicting the conjectured (O(\log N)) cap.

### C2. Finite‑bit ADS reconstruction (finite band)

Let (\widehat\mu(\tau)=\sum_{k=1}^{K} e^{-i t_k \tau}) on a log‑window (U). For suitable choices of a finite angle set (\Phi), thresholds ({u_\ell}) with step (\Delta), and (\tau)-samples ({\tau_m}*{m\le M}) with (M=O(K)), the 1‑bit measurements (b(\tau_m;\phi,u*\ell)) determine (\widehat\mu(\tau_m)) to accuracy (\le \Delta) (up to a global real scale), hence determine ({t_k}) in that band under a mild minimum‑separation hypothesis.
*Status:* natural corollary of monotone thresholding + standard line‑spectral identifiability on non‑uniform grids; making constants explicit would be new.

### C3. Cadence law (log‑time Kac–Rice)

Under the Gaussian model for (\widehat\mu_\varepsilon), the parity‑flip rate per unit (\tau) is (\nu_\tau=(1/\pi)\sqrt{-R''(0)}). For the common Lorentzian‑like (R(\Delta\tau)\approx \varepsilon^2/(\varepsilon^2+\Delta\tau^2)), one gets (\nu_\tau=\sqrt{2}/(\pi\varepsilon)) and (\Delta n_{\mathrm{flip}}\approx (\pi/\sqrt2)\varepsilon, n).
*Status:* standard application of the Kac–Rice formula; validating constants numerically for ADS is straightforward.

### C4. Paired‑variation convergence with spectral constant

There is a finite constant (C_\varepsilon) (expressible in terms of (\int (|\widehat\mu_\varepsilon|^2+|\widehat\mu_\varepsilon'|^2)e^{-\tau},d\tau)) such that
[
\sum_{m\ge 1}|B_m| \le C_\varepsilon,\qquad \sum_{m\ge1}|B_m|^2\le C_\varepsilon.
]
*Status:* follows from the two‑step expansion and basic regularity; making the spectral constant explicit is an analytic exercise.

### C5. Boundary mutual‑information positivity

Model “fiber + random complement” by (X(\tau)=\widehat\mu_\varepsilon(\tau)\mathbf 1_F(\tau)+W(\tau)\mathbf 1_{F^c}(\tau)) with (W) stationary Gaussian. Then the 1‑bit distribution on (F^c) near (\partial F) differs from the pure‑noise law, yielding a positive KL divergence and thus (I(F;,b|_{F^c})>0).
*Status:* formalizable with standard Gaussian comparison; quantifying the effect via midpoint/two‑step identities is a short calculation.

---

## 11. Practical protocol (numerical/experimental)

1. **Design.** Choose (\Phi={0}) (± pairing) or ({0,\pi/2}) (one‑sided). Fix thresholds (u_\ell) on ([-U,U]) with step (\Delta). Select (\tau)-samples (\tau_n=\log n) for (1\le n\le N_{\max}).

2. **Acquire bits.** Compute or measure (b(\tau_n;\phi,u_\ell)).

3. **Invert per (\tau_n).** Using last‑positive/first‑negative threshold, form (p(\tau_n,\phi)) and (\widetilde\mu(\tau_n)).

4. **Reconstruct ADS.** Either sum (\widetilde{\Delta A}_n) or use the midpoint formula (\widetilde A_N^{\mathrm{mid}}). Record errors vs. (\Delta/\sqrt n) and (\Delta/\sqrt N).

5. **Recover zeros (finite band).** Apply Prony / matrix‑pencil / ESPRIT to ({\widetilde\mu(\tau_m)}) to recover ({t_k}) in the band; verify stability under threshold refinement.

6. **Diagnostics.** (i) (E(N)/(K\log N)\to 1) (finite (K)); (ii) Rayleigh law for (|Z_N|); (iii) cadence flip‑rate per unit (\tau); (iv) decay and convergence of (B_m); (v) prime‑conditioned bumps near (n=p^m) (smoothed).

---

## 12. What is rigorous vs. heuristic (quick map)

* **Rigorous (finite (K); with damping for the full set).**
  Step identity; inversion; energy (K\log N+O(1)); Euler–Boole remainder and canonical scaling; half‑step law; two‑step residue; 1‑bit interval reconstruction; ADS readout with explicit error bounds; finite‑(K) identifiability from non‑uniform samples (classical line‑spectral theory).

* **Heuristic / testable.**
  Rayleigh law for (|Z_N|); cadence via Kac–Rice and its constants; prime‑conditioned annular bumps; boundary mutual information on noisy complements.

* **Conjectural (new).**
  ADS large‑sieve bound (E_w(N)\ll \log N) (⇒ RH); explicit constants in paired‑variation convergence; quantified boundary KL divergence; compressed 1‑bit schedules with near‑optimal bit budgets for finite‑band recovery.

---

## 13. Closing synthesis

* The ADS provides **exact, per‑step log–Fourier samples** of the zeta zero spectrum; after a canonical rescaling, it exhibits a Rayleigh (unitary) envelope with small arithmetic modulations.
* With symmetric (\pm t) pairing, the geometry **collapses to a line**; the dynamics is a fine left–right flicker governed by exact **midpoint** and **two‑step** identities.
* A **finite bundle of 1‑bit projections** is enough to reconstruct ADS on any finite window with explicit, quantitative error—and to recover the local spectrum via standard sparse exponential estimation.
* A short, **local (L^2)** inequality (ADS large–sieve) would **imply RH**, offering a concrete analysis target in this geometric, finite‑window language.

This package—exact identities, robust geometry, and a finite‑bit tomography scheme—gives a compact, falsifiable framework linking the zeta zeros’ spectral structure to a simple, observable “walk.”

