# Dirichlet Walk: Riemann Zeta Zeros on the Complex Plane
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
Compute the trajectory

Iteratively update:

𝑆
0
=
0
,
𝑆
𝑛
=
𝑆
𝑛
−
1
+
𝑀
𝑝
(
𝑛
)
 
𝑛
−
1
/
2
𝑒
−
𝑖
𝑡
𝑘
log
⁡
𝑛
.
S 
0
​
 =0,S 
n
​
 =S 
n−1
​
 +M 
p
​
 (n)n 
−1/2
 e 
−it 
k
​
 logn
 .
Code:

js
Copy code
z += Math.pow(n, -0.5) * M_p(n) * Math.exp(-i * t_k * Math.log(n));
points.push([Re(z), Im(z)]);
Each term is a complex vector of length 
1
/
𝑛
1
/
2
1/n 
1/2
 ,
rotated by angle 
𝑡
𝑘
log
⁡
𝑛
t 
k
​
 logn and optionally phase-flipped or rescaled by 
𝑀
𝑝
(
𝑛
)
M 
p
​
 (n).

Compute and visualize the walk

By the end of the loop, the script has all points

(
𝑥
𝑛
,
𝑦
𝑛
)
=
(
ℜ
𝑆
𝑛
,
ℑ
𝑆
𝑛
)
(x 
n
​
 ,y 
n
​
 )=(ℜS 
n
​
 ,ℑS 
n
​
 )
for each zero 
𝑡
𝑘
t 
k
​
  and mode 
𝑝
p.

These points trace a zeta spiral — a quasi-random walk whose step length decreases as 
1
/
𝑛
1
/
2
1/n 
1/2
 .

Analyze spatial and radial densities

The program then visualizes and measures:

𝐻
(
𝑥
,
𝑦
)
H(x,y): a 2-D heat map showing where the walk spends time (brightness ∝ density).

𝐷
(
𝑟
)
D(r): a 1-D radial density showing how often the walk crosses each radius 
𝑟
=
∣
𝑆
𝑛
∣
r=∣S 
n
​
 ∣.

Question
Given this definition of 
𝑆
𝑁
(
𝑡
𝑘
,
𝑝
)
S 
N
​
 (t 
k
​
 ,p) and the corresponding trajectories in the complex plane,
should we expect any particular geometric or statistical structure
(e.g., recurring radii, phase locking, or clustering)
to emerge as 
𝑁
→
∞
N→∞ or as 
𝑝
p varies?

What we found √p rings (discrete scale invariance)
Fix a zero 
𝑠
=
1
2
+
𝑖
𝑡
𝑘
s= 
2
1
​
 +it 
k
​
  and integer 
𝑝
≥
2
p≥2. With coefficients 
𝑎
𝑛
=
1
−
𝑝
⋅
1
𝑝
∣
𝑛
a 
n
​
 =1−p⋅1 
p∣n
​
 ,
the partial sums satisfy the two-scale identity

𝑆
𝑁
(
𝑠
,
𝑝
)
=
𝑇
(
𝑁
)
−
𝑝
1
−
𝑠
𝑇
(
⌊
𝑁
/
𝑝
⌋
)
,
𝑇
(
𝑥
)
=
∑
𝑛
≤
𝑥
𝑛
−
𝑠
.
S 
N
​
 (s,p)=T(N)−p 
1−s
 T(⌊N/p⌋),T(x)= 
n≤x
∑
​
 n 
−s
 .
Define 
𝑊
𝑁
:
=
𝑁
1
/
2
𝑒
𝑖
𝑡
𝑘
log
⁡
𝑁
𝑆
𝑁
(
𝑠
,
𝑝
)
W 
N
​
 :=N 
1/2
 e 
it 
k
​
 logN
 S 
N
​
 (s,p). Keeping the discrete boundary term, one obtains the asymptotic

𝑊
𝑁
=
−
𝑝
−
1
2
+
𝑂
(
𝑁
−
1
)
⇒
𝑊
𝑝
𝑀
=
𝑊
𝑀
+
𝑂
(
𝑀
−
1
)
.
W 
N
​
 =− 
2
p−1
​
 +O(N 
−1
 )⇒W 
pM
​
 =W 
M
​
 +O(M 
−1
 ).
Consequences:

self-similarity under 
𝑁
↦
𝑝
𝑁
N↦pN with scale 
𝑝
−
1
/
2
p 
−1/2
  and rotation 
−
𝑡
𝑘
log
⁡
𝑝
−t 
k
​
 logp,

log-periodic build-up in the radial density at radii forming a geometric ladder
𝑟
𝑚
∝
(
𝑝
)
 
𝑚
r 
m
​
 ∝( 
p
​
 ) 
m
  (enumerating outward by earlier steps; equivalently, for increasing 
𝑁
N: 
∣
𝑆
𝑝
𝑁
∣
≈
𝑝
−
1
/
2
∣
𝑆
𝑁
∣
∣S 
pN
​
 ∣≈p 
−1/2
 ∣S 
N
​
 ∣).
Stacking many zeros randomizes phase and leaves circular annuli at those radii.
For 
𝑝
=
2
p=2 (alternating case) adjacent rings are separated by a factor 
2
2
​
 .

The Dirichlet Walk Conjecture
Let the trajectory of a "Dirichlet Walk" be defined by the sequence of partial sums 
𝑆
𝑁
(
𝑠
,
𝑝
)
S 
N
​
 (s,p) in the complex plane, where:

𝑆
𝑁
(
𝑠
,
𝑝
)
=
∑
𝑛
=
1
𝑁
𝑀
𝑝
(
𝑛
)
⋅
𝑛
−
𝑠
,
with 
𝑀
𝑝
(
𝑛
)
=
{
1
−
𝑝
if 
𝑝
∣
𝑛
1
otherwise.
S 
N
​
 (s,p)= 
n=1
∑
N
​
 M 
p
​
 (n)⋅n 
−s
 ,with M 
p
​
 (n)={ 
1−p
1
​
  
if p∣n
otherwise.
​
 
A complex number 
𝑠
s generates a stable, origin-centered ring if the spatial density of the points in its trajectory forms a well-defined, high-density annulus centered at the origin.

The conjecture is that a complex number 
𝑠
s generates such a ring if and only if it is a zero of the function 
𝐿
(
𝑠
,
𝑝
)
=
(
1
−
𝑝
1
−
𝑠
)
𝜁
(
𝑠
)
L(s,p)=(1−p 
1−s
 )ζ(s).

This implies that the only numbers that produce this specific geometric signature are:

The non-trivial zeros of the Riemann zeta function, 
𝜁
(
𝑠
)
ζ(s).

The zeros of the factor 
(
1
−
𝑝
1
−
𝑠
)
(1−p 
1−s
 ), which lie on the line 
ℜ
(
𝑠
)
=
1
ℜ(s)=1.
