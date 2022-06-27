
---
title: variational free energy

---

The free energy can be expressed in three equivalent formulations:
$$
\begin{aligned}
F &= -\langle\ln p(y,x\mid m)\rangle_q + \langle \ln q(x\mid\mu)\rangle_q & &\quad \text{Energy minus entropy} \\
&= D_{\text{KL}}(q(x\mid\mu)\mid\mid p(x\mid y,m))-\ln p(y\mid m) & &\quad \text{Divergence plus surprisal}\\
&= D_{\text{KL}}(q(x\mid\mu)\mid\mid p(x\mid m))-\langle\ln p(y\mid x,m)\rangle_q & &\quad \text{Complexity minus accuracy}
\end{aligned}
$$
where $D_{\text{KL}}$ is the Kullback-Leibler divergence and $\langle*\rangle_q$ indicates the expected value under $q$.


