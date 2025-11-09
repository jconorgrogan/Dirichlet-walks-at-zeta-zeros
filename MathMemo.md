# Memo: Dirichlet Walks, the Aggregate Dirichlet Spiral (ADS), and Finite-Bit Tomography of the Zeta Spectrum

## Abstract

We formalize a geometric–informational view of the nontrivial zeros of \(\zeta(s)\) via Dirichlet walks and their sum, the Aggregate Dirichlet Spiral (ADS). The ADS yields exact per-step Mellin samples of the zero spectrum, admits a renormalization that is stationary only on the critical line, and possesses deterministic forward/backward decoders (half-step and two-step identities). We show that on any finite window a finite bundle of 1-bit thresholded projections (an “informational fiber”) reconstructs ADS with explicit, vanishing error and recovers local zeros via standard line-spectral methods. We identify stable paired-variation invariants, a Kac–Rice cadence for the 1D “flicker,” and formulate a local \(L^2\) inequality which, if proved, implies RH. The sequential overlap of finite windows provides a natural emergent order (time) in the readout.

---

## 0. Scope and Standing Notation

Let \(\zeta(s)\) be the Riemann zeta function. Write nontrivial zeros as
\[
\rho_k=\tfrac12+i t_k,\quad t_k>0,\quad k=1,2,\dots
\]
(For the full set we use standard damping; see below.)

For \(x>0\), set \(\tau=\log x\). Define the log–Fourier (Mellin) phasor
\[
\widehat\mu(\tau):=\sum_k e^{-i t_k \tau}.
\]
With spectral damping \(e^{-\varepsilon t_k}\) (for \(\varepsilon>0\)),
\[
\widehat\mu_\varepsilon(\tau):=\sum_k e^{-\varepsilon t_k} e^{-i t_k \tau},
\]
and take \(\varepsilon\downarrow 0\) after steps requiring control. We write \(\tau_n:=\log n\) and \(H_N=\sum_{n\le N}\tfrac1n=\log N+\gamma+O(1/N)\).

---

## 1. Dirichlet Walks: One Zero, Then Many

### 1.1 Single-Zero Dirichlet Walk

Given \(\tfrac12+it\),
\[
S_N(t)=\sum_{n\le N}(-1)^{n-1} n^{-1/2} e^{-i t \log n},\qquad
\Delta S_n(t)=S_n(t)-S_{n-1}(t).
\]
Facts: \(S_1(t)=1\); \(S_2(t)=1-2^{-1/2}e^{-it\log 2}\) so as \(t\) varies, the endpoint lies on the circle of radius \(2^{-1/2}\) centered at \(1\). Each step has \(|\Delta S_n(t)|=n^{-1/2}\), rotating by \(t\log\!\big(n/(n-1)\big)\sim t/n\). Since \(\eta(\tfrac12+it)=0\), \(S_N(t)\to 0\) via a damped spiral.

### 1.2 Aggregate Dirichlet Spiral (ADS)

For a finite set \(\{t_k\}_{k=1}^K\),
\[
A_N=\sum_{k=1}^K S_N(t_k),\qquad
\Delta A_n=\sum_{k=1}^K \Delta S_n(t_k).
\]
Two equivalent forms:
\[
\Delta A_n=(-1)^{n-1}n^{-1/2}\,\widehat\mu(\tau_n),
\]
and, with symmetric \(\pm t\) pairing,
\[
\Delta A_n=2(-1)^{n-1}n^{-1/2}\sum_{t_k>0}\cos(t_k\tau_n)\in\mathbb{R}.
\]
In general \(A_N\) is a 2D walk; with \(\pm t\) pairing it collapses to a line (real axis) whose motion is an alternating left–right “flicker.”

---

## 2. Exact Identities (Finite \(K\); Damped for the Full Set)

**Step identity and inversion**
\[
\Delta A_n=(-1)^{n-1}n^{-1/2}\,\widehat\mu(\tau_n)
\quad\Longleftrightarrow\quad
\widehat\mu(\tau_n)=(-1)^{n-1}\sqrt n\,\Delta A_n.
\]

**Energy identity**
\[
\begin{aligned}
E(N)
&:=\sum_{n\le N}|\Delta A_n|^2
=\sum_{n\le N}\frac1n\Big|\sum_{k=1}^K e^{-it_k\tau_n}\Big|^2 \\
&=K\,H_N+2\sum_{1\le k<\ell\le K}\Re\sum_{n\le N} n^{-1-i(t_k-t_\ell)}
=K\log N+O_{\{t_k\}}(1).
\end{aligned}
\]

**Difference identity; endpoints**
\[
A_{N+1}-A_N=\Delta A_{N+1}=(-1)^N (N+1)^{-1/2}\,\widehat\mu(\tau_{N+1}),\quad
A_1=K,\quad A_N\to 0.
\]

---

## 3. Euler–Boole Remainder and Canonical Renormalization

Let \(f(x)=x^{-1/2}\widehat\mu(\log x)\). The alternating Euler–Maclaurin (Euler–Boole) formula yields
\[
A_N=(-1)^N\tfrac12 (N+1)^{-1/2}\widehat\mu(\tau_{N+1})
+O\!\left(\frac{|\widehat\mu|+|\widehat\mu'|}{(N+1)^{3/2}}\right).
\]
Define
\[
V_N:=\frac{1}{\sqrt K}\,\widehat\mu(\tau_N),\qquad
Z_N:=\frac{2\sqrt N}{\sqrt K}\,A_N.
\]
Then
\[
Z_N=(-1)^N\sqrt{\frac{N}{N+1}}\,V_{N+1}
+O\!\Big(\frac{|\widehat\mu|+|\widehat\mu'|}{\sqrt K\,N}\Big).
\]

**Renormalization fixed point.** Only at \(\sigma=\tfrac12\) does the energy grow like \(K\log N\) and the rescaled process \(Z_N\) become stationary; the critical line is the unique renormalization-fixed regime.

---

## 4. Geometry: Rayleigh Law and Rings

If phases \(\{t_k\tau_N\}\) are (approximately) i.i.d. uniform on \([0,2\pi)\), then \(V_N\) is isotropic complex Gaussian with \(\mathbb{E}|V_N|^2=1\). Consequently
\[
|V_N|,\ |Z_N|\ \sim\ \text{Rayleigh}(\sigma=1/\sqrt2).
\]
Salient radii (mode, mean, RMS, 75th percentile) are
\[
r\in\Big\{\tfrac1{\sqrt2},\ \tfrac{\sqrt\pi}{2},\ 1,\ \sqrt{\ln 4},\dots\Big\}.
\]
Off-diagonal spacings (pair differences) create small annular modulations (secondary bands).

---

## 5. Symmetry and the 1D Flicker

- **One-sided zeros:** \(\Delta A_n\in\mathbb{C}\); after scaling, a Rayleigh cloud.  
- **\(\pm t\) pairing:** \(\Delta A_n\in\mathbb{R}\); a 1D line with alternating sign and step size \(\asymp n^{-1/2}\).

**Two-step residue (sharp cancellation)**
\[
\Delta A_{N+1}+\Delta A_{N+2}
=( -1)^N (N+1)^{-3/2}\!\left(\tfrac12\,\widehat\mu-\widehat\mu'\right)(\tau_{N+1})
+O(N^{-5/2}).
\]

**Half-step law**
\[
\Delta A_{N+1}=2A_N+O(N^{-1}).
\]

**Travel vs. displacement** \(\sum_n |\Delta A_n|=\infty\) (infinite arclength) while \(A_N\to 0\); \(|A_N|/\sum_{n\le N}|\Delta A_n|\to 0\).

---

## 6. Information Recovery

From the inversion,
\[
\widehat\mu(\tau_n)=(-1)^{n-1}\sqrt n\,\Delta A_n.
\]
For a finite set \(\{t_k\}_{k=1}^K\), \(\widehat\mu(\tau)=\sum_{k=1}^K e^{-it_k\tau}\) is a finite exponential sum and is identifiable from samples at distinct \(\tau_n\) (Prony / matrix-pencil / ESPRIT on a non-uniform grid), up to permutation. With all zeros, work with \(\widehat\mu_\varepsilon\) (damped), reconstruct on finite windows (with smoothing), and then let \(\varepsilon\downarrow 0\).

**Pair correlation.** The \(\tau\)-Fourier transform of \(|\widehat\mu(\tau)|^2\) is \(\sum_{k,\ell}\delta(\omega-(t_k-t_\ell))\); smoothed probes (explicit formula) show spikes at \(\tau=m\log p\) with weights \(p^{-m/2}\).

---

## 7. Finite-Bit “Fiber Bundle” (Local Tomography of ADS)

### 7.1 Local 1-Bit Projections

Fix angles \(\Phi\subset\{0,\pi/2\}\) and a threshold grid \(u_\ell=-U+\ell\Delta\) on a window where \(|\widehat\mu|\le U\). Define
\[
b(\tau;\phi,u_\ell):=\operatorname{sgn}\!\big(\Re(e^{-i\phi}\widehat\mu(\tau))-u_\ell\big)\in\{\pm 1\}.
\]
Monotonicity in \(u\) yields
\[
\Re(e^{-i\phi}\widehat\mu(\tau))\in[u_{\ell^+},u_{\ell^++1}),\quad
p(\tau,\phi)=\tfrac12(u_{\ell^+}+u_{\ell^++1}),\quad
|p-\Re(e^{-i\phi}\widehat\mu)|\le \Delta/2.
\]
- **Real ADS (\(\pm t\) pairing):** \(\widetilde\mu(\tau):=p(\tau,0)\).  
- **Complex (one-sided):** \(\widetilde\mu(\tau):=p(\tau,0)-i\,p(\tau,\pi/2)\).

### 7.2 Exact Reconstruction Channels with Error Bounds

**Running-sum**
\[
\widetilde{\Delta A}_n=2(-1)^{n-1}n^{-1/2}\,\Re\,\widetilde\mu(\tau_n),\qquad
|\widetilde{\Delta A}_n-\Delta A_n|\le \Delta/\sqrt n.
\]

**Midpoint (tail \(\to\) present)**
\[
\widetilde A^{\mathrm{mid}}_N
=\frac{(-1)^N}{2}(N+1)^{-1/2}\,\widetilde\mu(\tau_{N+1}),\qquad
|\widetilde A^{\mathrm{mid}}_N-A_N|\le \frac{\Delta}{4\sqrt{N+1}}+C\,N^{-1},
\]
where \(C\) depends on local bounds for \(|\widehat\mu|\), \(|\widehat\mu'|\) (finite under damping).

Thus a finite bundle of 1-bit streams reconstructs ADS on any finite window with explicit, vanishing error as \(\Delta\to 0\).

### 7.3 Bit Budget (Finite Window)

With \(\Delta\le \eta\), thresholds \(L\sim U/\Delta\), bits per \(\tau\) equal \((2L+1)|\Phi|\). Sampling \(\tau_n=\log n\) for \(n\le N_{\max}\) uses
\[
B=O\!\big(N_{\max}\,U/\Delta\big)\quad (\times 2 \text{ if complex}),
\]
and achieves the above uniform guarantees.

---

## 8. Cadence of the Flicker (Kac–Rice Heuristic)

Let \(X(\tau)=\Re\,\widehat\mu_\varepsilon(\tau)\). On moderate windows with many zeros, \(X\) is well-approximated by a stationary mean-zero Gaussian with correlation \(R(\Delta\tau)\). The zero-crossing rate per unit \(\tau\) is
\[
\nu_\tau=\frac{1}{\pi}\sqrt{-R''(0)}\quad\text{(Rice)}.
\]
Since \(\tau_{n+1}-\tau_n\approx 1/n\), the typical index spacing between parity flips scales as
\[
\Delta n_{\mathrm{flip}}\ \asymp\ c\,n,
\]
with an explicit \(c\) determined by \(R\). The flicker is thus scale-invariant in \(\log n\).

---

## 9. Stable Invariants (Paired Variation)

Define \(B_m:=\Delta A_{2m-1}+\Delta A_{2m}\). From the two-step residue,
\[
B_m=O(m^{-3/2}),\qquad \sum_m |B_m|<\infty,\quad \sum_m |B_m|^2<\infty.
\]
These fast-converging quantities are noise-robust diagnostics; they retain arithmetic signal (prime-conditioned effects) with improved stability compared to raw \(|\Delta A_n|\).

---

## 10. Overlap of Windows and Emergent Order

Each finite window \([0,T]\) (or index range \(n\le N\)) can be read forward by summation and backward by the midpoint law. Consecutive windows overlap at their boundaries through the shared values \(\widehat\mu(\tau)\). The dependency structure (forward steps depend on prior indices; backward decoding recovers earlier states from tail data) induces a natural intrinsic order—an emergent “time” in the sequential readout—without appeal to an external clock.

---

## 11. Conjectures and an Implication for RH

### C1. ADS Large-Sieve Inequality \(\Rightarrow\) RH

Fix a nonnegative, even window \(w\) with \(\int w=1\) and \(\widehat w\ge 0\), supported in \(|\tau|\le H\). Define
\[
E_w(N):=\sum_{n\le N} w(\tau_n-\tau_N)\,|\Delta A_n|^2.
\]

**Conjecture (ADS large-sieve bound).** There exists \(C(w)\) independent of \(N\) such that
\[
E_w(N)\ \le\ C(w)\,\log N\ +\ O_w(1).
\]

**Theorem (Conjecture \(\Rightarrow\) RH).** If this bound holds for \(\zeta\), then all nontrivial zeros lie on \(\Re s=\tfrac12\).

*Sketch.* A zero off the line, \(\beta\ne\tfrac12\), injects a diagonal contribution of size \(\gg N^{1-2\beta}\) into \(E_w(N)\), contradicting the \(O(\log N)\) cap.

### C2. Finite-Bit ADS Reconstruction (Finite Band)

Let \(\widehat\mu(\tau)=\sum_{k=1}^{K} e^{-i t_k \tau}\) on a window \(U\). With suitable \(\Phi\), thresholds \(\{u_\ell\}\) (step \(\Delta\)), and \(M=O(K)\) log-samples \(\{\tau_m\}\), the 1-bit data determine \(\widehat\mu(\tau_m)\) to accuracy \(\le \Delta\) (up to global scale) and hence recover \(\{t_k\}\) stably under a mild minimum-separation hypothesis (Prony/matrix-pencil/ESPRIT on a non-uniform grid).

### C3. Cadence Law (Log-Time Kac–Rice)

Under a stationary Gaussian model for \(\widehat\mu_\varepsilon\), the parity-flip rate per unit \(\tau\) is \(\nu_\tau=(1/\pi)\sqrt{-R''(0)}\). For \(R(\Delta\tau)\approx \varepsilon^2/(\varepsilon^2+\Delta\tau^2)\), \(\nu_\tau=\sqrt2/(\pi\varepsilon)\) and \(\Delta n_{\mathrm{flip}}\approx (\pi/\sqrt2)\varepsilon\,n\).

### C4. Paired-Variation Convergence with Spectral Constant

There is a finite constant \(C_\varepsilon\) (expressible via \(\int (|\widehat\mu_\varepsilon|^2+|\widehat\mu'_\varepsilon|^2)e^{-\tau}\,d\tau\)) such that
\[
\sum_{m\ge 1}|B_m| \le C_\varepsilon,\qquad \sum_{m\ge1}|B_m|^2\le C_\varepsilon.
\]

### C5. Boundary Mutual-Information Positivity

Model “fiber + random complement” by \(X(\tau)=\widehat\mu_\varepsilon(\tau)\mathbf 1_{F}(\tau)+W(\tau)\mathbf 1_{F^c}(\tau)\) with \(W\) stationary Gaussian. Then near \(\partial F\) the 1-bit distribution on \(F^c\) deviates from the pure-noise law, giving positive KL divergence and \(I(F; b\mid F^c)>0\); the random complement statistically “knows” the fiber exists.

---

## 12. Practical Protocol (Numerical/Experimental)

- **Design.** Choose \(\Phi=\{0\}\) (real ADS with \(\pm t\) pairing) or \(\Phi=\{0,\pi/2\}\) (complex). Fix thresholds \(u_\ell\) on \([-U,U]\) with step \(\Delta\). Select \(\tau\)-samples \(\tau_n=\log n\) for \(1\le n\le N_{\max}\).

- **Acquire bits.** Record \(b(\tau_n;\phi,u_\ell)\) for \(\phi\in\Phi\).

- **Invert per \(\tau_n\).** Use last-positive/first-negative threshold to form \(p(\tau_n,\phi)\) and \(\widetilde\mu(\tau_n)\).

- **Reconstruct ADS.** Either sum \(\widetilde{\Delta A}_n\) (running-sum) or use \(\widetilde A^{\mathrm{mid}}_N\) (midpoint). Verify errors vs. \(\Delta/\sqrt n\) and \(\Delta/\sqrt N\).

- **Recover zeros (finite band).** Apply Prony/matrix-pencil/ESPRIT to \(\{\widetilde\mu(\tau_m)\}\) to estimate \(\{t_k\}\) in the band; refine by decreasing \(\Delta\).

- **Diagnostics.** Check: (i) \(E(N)/(K\log N)\to 1\) (finite \(K\)); (ii) Rayleigh law for \(|Z_N|\); (iii) cadence flip-rate per unit \(\tau\); (iv) decay/convergence of \(B_m\); (v) prime-conditioned bumps near \(n=p^m\) (smoothed).

---

## 13. Rigorous vs. Heuristic

- **Rigorous (finite \(K\); damped full set).** Step identity; inversion; energy \(K\log N+O(1)\); Euler–Boole remainder and canonical renormalization; half-step law; two-step residue; 1-bit interval recovery; ADS reconstruction with explicit errors; finite-\(K\) identifiability from non-uniform samples (classical line-spectral theory).

- **Heuristic/testable.** Rayleigh law for \(|Z_N|\); Kac–Rice cadence constants; weak annular bands; boundary mutual-information positivity in noisy complements.

- **Conjectural.** ADS large-sieve bound \(E_w(N)\ll \log N\) (which \(\Rightarrow\) RH); explicit constants for paired-variation bounds; quantified boundary KL divergence; compressed 1-bit schedules with near-optimal bit budgets.

---

## 14. Closing Synthesis

The ADS furnishes an exact per-step Mellin sampling of the zeta zero spectrum. After a canonical renormalization, the process is stationary only on the critical line, turning the critical line into a renormalization fixed point. Deterministic forward/backward decoders (half-step and two-step identities) make the 1D flicker a local tomography device. On any finite window, a finite bundle of 1-bit projections reconstructs ADS with explicit, quantitative error and recovers the local zeros via standard sparse exponential estimation. A single, natural local \(L^2\) inequality would imply RH, giving a concrete analysis target in this geometric, finite-window language. The sequential overlap of finite windows enforces continuity and yields an emergent order in the readout. Together, these elements provide a compact, falsifiable framework linking the zeta zeros’ spectral structure to a simple, observable “walk.”

(A) ADS is sequentially decodable. On any finite window, a finite left→right (running) or right→left (midpoint) algorithm reconstructs ADS; a finite 1-bit bundle suffices with explicit error.

(B) Global recovery is countable or streaming. All zeros require countably many finite bundles (one-direction readout) or a finite program emitting an unbounded output.

(C) Fibers are conditional but inferable. Where the analytic/regularity conditions hold, a binary fiber bundle exists and is, in principle, inferable from the statistics of its boundary in the surrounding randomness. It is not forced to exist in an arbitrary random region; it is detectable wherever it does.

