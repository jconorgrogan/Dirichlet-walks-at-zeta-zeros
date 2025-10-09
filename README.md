# Visual-of-5000-Riemann-zeta-zeros-alternating--series-on-complex-plane

A (to my knowledge) unique/novel way of visualizing the zeta zeros 

<img width="480" height="954" alt="image" src="https://github.com/user-attachments/assets/f6268d77-71cf-4509-8c1d-f512be9cdeae" />

<img width="697" height="683" alt="image" src="https://github.com/user-attachments/assets/8c671482-fbfd-49a8-9c8a-062e60ff855d" />

This project visualizes the complex-plane trajectories of partial sums evaluated at nontrivial Riemann zeta zeros.

For each zero ρₖ = ½ + itₖ and mode parameter p, we compute:

$$S_N(t_k, p) = \sum_{n=1}^{N} M_p(n) \cdot n^{-1/2} \cdot e^{-i t_k \log n}$$

where the multiplier is:

$$M_p(n) = \begin{cases}
1 - p, & \text{if } p \mid n \\
1, & \text{otherwise}
\end{cases}$$

### The √p Depletion Pattern

Heat maps of spatial density reveal **systematic rings at radius r = √p** for each mode p, eg for the alternating series we see a dark ring form at sqrt(2) where each and every walk "orbits"
