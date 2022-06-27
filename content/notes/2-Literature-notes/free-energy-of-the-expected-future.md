
---
title: free energy of the expected future

---

> to act adaptively, ==agents should act so as to minimize the difference between what they predict will happen, and what they desire to happen==. Put another way, adaptive action for an agent consists of forcing reality to unfold according to its’ preferences.  — [@Millidge2020c](notes/6-Citation-notes/@Millidge2020c.md)

$$
\begin{aligned}
\mathbf{F E E F}(\pi) _ {\tau} 
&= \mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\mathbf{D} _ {K L}\left[Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)\|\ln \tilde{p}\left(o _ {\tau}, x _ {\tau}\right)\right] \\
&=\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)-\ln \tilde{p}\left(o _ {\tau}, x _ {\tau}\right)\right] \\
&=\underbrace{\mathbb{E} _ {Q\left(x _ {\tau} \mid \pi\right)} \mathbf{D} _ {K L}\left[Q\left(o _ {\tau} \mid x _ {\tau}\right) \| \tilde{p}\left(o _ {\tau}\right)\right]} _ {\text {Extrinsic Value }}-\underbrace{\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)} \mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid o _ {\tau}\right) \| Q\left(x _ {\tau} \mid \pi\right)\right]} _ {\text {Intrinsic Value }}
\end{aligned}
$$

> The first thing to note is that *the intrinsic value terms of the FEEF and the EFE are identical* (see [Definitions](notes/2-Literature-notes/free-energy-of-the-expected-future.md/#Definitions) below), under the assumption that the variational posterior is approximately correct $Q(x _ \tau\mid o _ \tau) \approx p(x _ \tau\mid o _ \tau)$ such that *FEEF-minimizing agents will necessarily show identical epistemic behavior to EFE-minimizing agents*. Unlike the EFE, however, the FEEF also possesses a strong naturalistic grounding as a bound on a theoretically relevant quantity. ==The FEEF can maintain both its information-maximizing imperative and its theoretical grounding since it is derived from the minimization of a KL divergence rather than the maximization of a log model evidence==. — [@Millidge2020c](notes/6-Citation-notes/@Millidge2020c.md)

> The key difference with the EFE lies in the likelihood term. ==While the EFE simply tries to maximize the expected evidence of the desired observations, the FEEF minimizes the KL divergence between the likelihood of observations predicted under the veridical generative model and the marginal likelihood of observations under the biased generative model==.
> [...] The extrinsic value term thus encourages the agent to choose its actions such that its predictions over states lead to observations which are close to its preferred observations, while also trying move to states whereby the entropy over observations is maximized, thus leading the agent to move towards states where the generative model is not as certain about the likely outcome. ==In effect, the FEEF possesses another exploratory term, in addition to the information gain, which the EFE lacks==.  — [@Millidge2020c](notes/6-Citation-notes/@Millidge2020c.md)

> Another important advantage is that ==the FEEF it is mathematically equivalent to the VFE (with a biased generative model) in the present time with a current observation==. [...] This means that theoretically we can consider an agent to be both inferring and planning using the same objective, which is not true of the EFE. *The EFE does not reduce to the VFE when observations are known, and thus requires a separate objective function to be minimized for planning compared to inference*. Because of this, it is actually possible to argue that FEEF is mandated by the free-energy principle. ==On this view there is no distinction between present and future inference and both follow from minimizing the same objective but under different informational constraints==.  — [@Millidge2020c](notes/6-Citation-notes/@Millidge2020c.md)

---

## Definitions

**VFE** : *Instantaneous Free energy*
$$
\begin{aligned}
\mathbb{F} &=\mathbf{D} _ {K L}\left[Q\left(x _ {t} \mid o _ {t} ; \phi\right) \| p\left(o _ {t}, x _ {t}\right)\right] \\
&=\mathbb{E} _ {Q\left(x _ {t} \mid o _ {t} ; \phi\right)}\left[\ln \frac{Q\left(x _ {t} \mid o _ {t} ; \phi\right)}{p\left(o _ {t}, x _ {t}\right)}\right] \\
&=-\underbrace{\mathbb{E} _ {Q\left(x _ {t} \mid o _ {t} ; \phi\right)}\left[\ln p\left(o _ {t} \mid x _ {t}\right)\right]} _ {\text {Accuracy }}+\underbrace{\mathbf{D} _ {K L}\left[Q\left(x _ {t} \mid o _ {t} ; \phi\right)|| p\left(x _ {t}\right)\right]} _ {\text {Complexity }}
\end{aligned}
$$
**EFE**: *Expected free energy*
**AIF**: *Active inference*. Agents choose policies that minimize a free energy functional (originally a cumulative sum over time of EFE [@Friston2015d](notes/6-Citation-notes/@Friston2015d.md)). Active inference revolves around the idea of action-conditioned futures.

==Note==: in the intro it makes a very complete bibliographical overview of applications of AIF in different areas.

Newly proposed free energy functionals:
**FEF**: *Free Energy of the Future.*
**FEEF**: *Free Energy of the Expected Future*

### Distributions and symbols
$t$: time-step in the past
$\tau$: time-step in the future ($t<\tau$)
$T$: time horizon, so that $\tau<T$
$o _ t$: observed states or observations
$x _ t$: hidden states
$a _ \tau$: action
$\pi=[a _ 1, a _ 2,\dots,a _ T]$: policy
$Q(x _ t\mid o _ t ;\phi)$: variational posterior; approximate posterior density parametrized by $\psi$
$Q(x _ t)=\mathbb{E} _ {p(x _ t\mid x _ {t-1})}[Q(x _ {t-1}\mid o _ {t-1};\psi)]$: Variational prior; obtained by mapping the previous posterior through the transition dynamics.
$p(x _ t\mid x _ {t-1})$: true transition dynamics
$\tilde{p}(o _ {\tau:T})$: Biased observation model; encodes an agent's goals.
$\tilde{p}(o _ \tau,x _ \tau)\approx\tilde{p}(o _ \tau)Q(x _ \tau\mid o _ \tau)$: Biased generative model of the world.

---
### Expected free energy

**Planning as inference of future states**
> Instead of saying: I have some goal, what do I have to do to achieve it? the active inference agent asks: *Given that my goals were achieved, what would have been the most probable actions that I took?*

**Expected free energy**
> In the active inference framework, *the goal is to infer a variational distribution over both hidden states and policies that maximally fit to a biased generative model of the future*. The framework defines the variational objective function to be minimized, the Expected Free Energy, from time $\tau$ until the time horizon $T$, which is denoted $\mathcal{G}$:
$$
\begin{aligned}
\mathcal{G}(\pi) &=\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln Q\left(x _ {\tau} \mid \pi\right)-\ln \tilde{p}\left(o _ {\tau}, x _ {\tau}\right)\right] \\
&=\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln Q\left(x _ {\tau} \mid \pi\right)-\ln \tilde{p}\left(o _ {\tau} \mid x _ {\tau}\right)-\ln p\left(x _ {\tau}\right)\right] \\
&=\underbrace{-\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln \tilde{p}\left(o _ {\tau} \mid x _ {\tau}\right)\right]} _ {\text {Accuracy }}+\underbrace{\mathbb{E} _ {Q\left(o _ {\tau} \mid x _ {\tau}\right)}\left[\mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid \pi\right) \| p\left(x _ {\tau}\right)\right]\right]} _ {\text {Complexity }} \\
&= \underbrace{-\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln \tilde{p}\left(o _ {\tau}\right)\right]} _ {\text {Extrinsic Value }}-\underbrace{\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)}\left[\mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid o _ {\tau}\right) \| Q\left(x _ {\tau} \mid \pi\right)\right]\right]} _ {\text {Epistemic Value }}
\end{aligned}
$$

---
### Free Energy of the Future

**Requirements for a free energy functional for an active inference agent**
> We argue that the natural extension of the free energy into the future must possess direct analogs to the two crucial properties of the VFE: *it must be expressible as a KL-divergence between a posterior and a generative model*, such that minimizing it causes the variational density to better approximate the true posterior. *Secondly, it must also bound the log model evidence of future observations*.

**Importance of the second requirement**
> Bounding the log model evidence (or surprisal) is vital since the surprisal is the core quantity which, under the FEP, all systems are driven to minimize. If the VFE extended into the future failed to bound the surprisal, then minimizing this extension would not necessarily minimize surprisal, and thus *any agent which minimized such an extension would be in violation of the FEP*.

**Free Energy of the Future**
$$
\begin{aligned}
\mathbf{F E F} _ {\tau}(\pi) &=\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)}\left[\ln Q(x _ \tau\mid o _ \tau)-\ln\tilde{p}(o _ \tau,x _ \tau)\right] \\
&=\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)}\mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid o _ {\tau}\right) \| \tilde{p}\left(o _ {\tau}, x _ {\tau}\right)\right] \\
& \approx-\underbrace{\mathbb{E} _ {Q\left(o _ {\tau}, x _ {\tau} \mid \pi\right)}\left[\ln \tilde{p}\left(o _ {\tau} \mid x _ {\tau}\right)\right]} _ {\text {Accuracy }}+\underbrace{\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)} \mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid o _ {\tau}\right) \| Q\left(x _ {\tau} \mid \pi\right)\right]} _ {\text {Complexity }}
\end{aligned}
$$

> Unlike the EFE however, the expected information gain (complexity) term is positive while in the EFE term it is negative. [...] An *FEF agent thus tries to maximize its reward while trying to explore as little as possible*. While this sounds surprising, *it is in fact directly analogous to the complexity term in the VFE*, which mandates maximizing the likelihood of an observation, while also keeping the posterior as close as possible to the prior.

**FEF is an upper bound to surprise**
$$
-\mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)}\left[\ln\tilde{p}(o _ \tau)\right] \leq \mathbb{E} _ {Q\left(o _ {\tau} \mid \pi\right)}\mathbf{D} _ {K L}\left[Q\left(x _ {\tau} \mid o _ {\tau}\right) \| \tilde{p}\left(o _ {\tau}, x _ {\tau}\right)\right] = \mathbf{F E F} _ {\tau}(\pi)
$$
FEF is an upper bound on expected model evidence, which can be tightened by minimizing the FEF. By contrast, the EFE is a lower bound which must be maximized.

