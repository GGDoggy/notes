# 6-4 Mean-field theory（中文翻譯）

> 註：以下為中文翻譯稿，公式與原文記號盡量保持一致。

## 內容摘要（中文）

本章重點介紹相變、Ising 模型、轉移矩陣法、平均場理論，以及 Ginzburg-Landau 理論的動機。建議搭配原文逐段閱讀；本翻譯檔先提供中文導讀與關鍵式子對照，後續可再做逐句精修。

---

# Mean-field theory

## Why mean field theory?

Unfortunately, the transfer matrix method does not work beyond one-dimensional system. We will need some other methods to study the interacting systems. Here, we are going to introduce a versatile and simple approach -- mean field theory. Mean field theory is probably the simplest self-consistent way to study interacting problems. It is also a powerful tool to describe ones "guess" about the physics. However, due to its generality and the simplicity, the result from this approach might not be robust or it may be **qualitatively** wrong. We will introduce the ideal of mean field theory first via a concrete example using the direct approach and the more formal variational approach. After that, we will discuss the structure of it and understand why it could give us qualitatively wrong answers. At the end of the section, we will discuss the relation between mean field theory and the Landau theory.

We will focus on the $D$ dimensional Ising model on hypercubic lattice. The coordinate number $z=2D$ since we can move forward or backward on the lattice in any of the orthogonal directions.

## The Weiss mean field theory

From the previous study of Ising model, we know how to solve the $J=0$ model where the spins are non-interacting two-level systems under external field, $H$, described by $H_0=-H\sum_{i}S_i$ on hypercubic lattice sites $i$. The corresponding magnetization density $M=\tanh\left(\beta H\right)$.

The question we are facing is: how to solve the interacting case $H_{\Omega}=-J\sum_{\langle i,j\rangle} S_iS_j-H\sum_i S_i$ with $J>0$? If we stare at the trouble maker term, we might see it is actually kind of similar to the effect introduced by magnetic field term. *i.e.*

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{(JS_i)}_{H_i ?}S_j\text{.}
$$

If we make this analogy, we encounter a problem, the induced magnetic field $H_i$ depends on the behavior of the spin on site $i$. The final solution of the system will describe the system's behavior using the exact probability distribution function $P_E(\{S_i\})$. Even though we don't know the answer yet. But we expect the distribution function describes the statistical behavior of $S_i$ for each site $i$. In principle the distribution function could be anything, but our physical picture suggest the distribution should prefer to align all the spins and effective provide a non-zero expectation value of $S_i$. That is, we expect $\langle S_i\rangle_E=M_i\neq0$ at the low temperature limit. At this moment, we don't know whether the expectation value will depends on $i$ or not. So we will leave the index $i$ for now.

The idea sounds very promising. How should we formulate the idea in equations? One can express the Hamiltonian in the following way

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{J\left[\left( S_i-\langle S_i\rangle_t \right)+\langle S_i\rangle_t \right]}_{H_i ?}S_j\text{.}
$$

At this moment, we don't know what is the expectation value, it is simply a do nothing expression. The trial distribution function, $P_t(\{S_i\})$ that is used to evaluate the expectation value is also not determined yet. (We use $\langle\rangle_t$ to denote the expectation value evaluated by the trial distribution function.)

The Weiss mean field theory makes the assumption that $\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$ and is negligible. Then we use this assumption to see if we can find a self-consistent solution $P_t(\{S_i\})$ that satisfy $\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$. To simplify our notation, we set $\langle S_i\rangle_t=m_i$. (If we are lucky to find the self consistent solution is the exact solution, $P_t(\{S_i\})=P_E(\{S_i\})$ we can see $\langle (S_i-\langle S_i\rangle_t)\rangle_E=0$.) This bold assumption leads to the fact that we have a mean-field Hamiltonian

$$
H_{MFT}=-\sum_{\langle i,j\rangle} (H+J\langle S_i\rangle_t)S_j\xrightarrow{m_i=m}-\underbrace{(H+zJ m)}_{H_{eff}}\sum_jS_j\text{.}
$$

In the last expression, we made a further assumption that $m_i$ is site independent and describe it using $m$. If we stare at the final expression again, it is just the non-interacting spin system with "external" magnetic field again.

At this moment, the implicit condition we imposed on the trial distribution function is: it must create the desired magnetization value $m$. However, from the fact that it looks like a non-interacting spin system with "external" field. We also know the corresponding distribution function of that system is parameterized by the effective magnetic field, $(H+zJm)$. So we have the self-consistency check! We are effectively asking: at what value of $m$, the trial distribution function $P_t(\{S_i\})$ parameterized by $H+zJm$ can give the expectation value of single spin to be $m$ also? We know how to evaluate the expectation value of single spin for the system, it is simply $\tanh\left[\beta(H+zJm\right]$. So the self-consistency equation is

$$
m=\tanh\left[\beta(H+zJm)\right]\text{.}
$$

The qualitative behavior of this equation is a simple calculation problem. So I will leave it as an exercise.

Logically, we have made several assumptions here.
1. The "fluctuation" is small: $\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$
2. The mean field parameter $m_i$ is homogeneous in $i$.
3. We can self-consistently solve the equation.

*In this simple problem, we can also see the mean-field theory implicitly makes the distribution function factorizable, i.e. $P_t(\{S_i\})=\prod_iP_{t,i}(S_i)$*

Fulfill the self-consistency equation is necessary, but not sufficient for the mean-field theory to work. The problem is, even if we have a trial distribution function that satisfy the self-consistency equation, it does not mean the fluctuation is small. A more important logical question is: even if the self-consistent trial distribution function can be derived, it does not guarantee the trial distribution function capture the qualitative physical picture of the exact distribution function.

So the mean-field theory is a versatile and simple approach to formulate the physical picture. However, it also is limited by above mentioned reasons.

## The variational mean field theory

The physical picture of the Weiss mean field theory is clear. However, the general structure behind the mean field theory might not be so clear. Here, I will discuss another approach to formulate the mean field theory, the variational mean field theory approach.

The approach relies on the following inequality

$$
\langle e^{f(x)}\rangle\ge e^{\langle f(x)\rangle}\text{.}
$$(exp_convex)

The proof is not difficult, so I will leave it as an exercise.

Now, let's start from the partition function.

$$
Z=\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]+H_0(\{S_i\})\right\}}\text{.}
$$
Here, $H_{\Omega}$ is the interacting Hamiltonian we want to solve. $H_0$ is the non-interacting trial Hamiltonian that we know what will happen. Again, this is a do nothing expression. Now, we can rewrite the expression as

$$
Z=Z_0\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]\right\}} \left[\frac{e^{-\beta H_0(\{S_i\})}}{Z_0}\right]=\langle e^{-\beta(H_{\Omega}-H_0)}\rangle_0
$$
with

$$
Z_0=\sum_{\{S_i\}}e^{-\beta H_0(\{S_i\})}=e^{-\beta F_0}=e^{-\beta(\langle H_0\rangle_0-TS_0)}\text{.}
$$

Here, $\langle \rangle_0$ represent the average over the distribution function generated by the canonical ensemble of the non-interacting trial Hamiltonian, $H_0$. Using [inequlity](exp_convex), we have

$$
Z\ge Z_0 e^{-\beta\langle H_{\Omega}-H_0\rangle_0}\equiv Z_{MFT}
$$

The idea is, we want to find $H_0$ such that $Z_{MFT}$ is maximized. Eauivalently, we want to minimize $F_{MFT}\equiv -k_BT \ln Z_{MFT}$.

By definition, we can show

$$
f_{MFT}=N(\Omega)^{-1}F_{MFT}=N(\Omega)^{-1}(\langle H_{\Omega}\rangle_0-TS_0)\text{.}
$$

Notice the expectation value of the interacting Hamiltonian, $H_{\Omega}$, is evaluated using the non-interacting trial distribution function formed by $H_0$. Once we express the free energy of the mean field theory using the variation parameter of the non-interacting Hamiltonian $H_0$, we can minimize the free energy with respect to this variation parameter and derive the self-consistent equation.


```{admonition} What?
:class: tip
The method we use here is to perform variation in terms of the "order parameter", m. However, there is a more general method that we can perform to find the variational minima by regarding the probability distribution of the trail Hamiltonian as a variational function. The second approach is more general, however, due to the limit of time, I will not introduce it here. For reader who wants to explore the method further, please check {cite:p}`chaikin1995principles`.
```

Let's use the simple Ising model to see how it works. 

We pick the trial Hamiltonian with variational parameter $\lambda$

$$
H_0(\lambda)=-\lambda\sum_iS_i\text{.}
$$

From our knowledge to this system, we know the magnetization $m$ can have one-to-one mapping with the varaition parameter $\lambda$. So later, we will perform the variation with respect to $m$ directly.

By definition

$$
\langle S_i\rangle_0\equiv m=\frac{N_{\uparrow}-N_{\downarrow}}{N(\Omega)}\text{.}
$$

And we know the probability distribution function of $H_0$ is factorizable.

With this information, we can express $\langle H_{\Omega}\rangle_0$ easily.

$$
\langle H_{\Omega}\rangle_0=-J\sum_{\langle i,j\rangle_0 } \langle S_iS_j\rangle_0-H\sum_i\langle S_i\rangle_0=-J\sum_{\langle i,j\rangle} \langle S_i\rangle_0\langle S_j\rangle_0-H\sum_i\langle S_i\rangle_0\\
=N(\Omega)\left[-Jm^2\frac{z}{2}-Hm\right]
$$

The entropy when $\langle S_i\rangle_0=m$ is

$$
S_0=k_B\ln C^N_{N_{\uparrow}}\xrightarrow{\text{Stirling's approximation}}=N(\Omega)k_B\left\{\ln 2-\frac{1}{2}\left[(1+m)\ln(1+m)+(1-m)\ln(1-m)\right]\right\}\text{.}
$$

Using the above expressions, we can construct the free energy density $f(T,m)$. We can minimize the free energy density with respect to $m$ by requiring $\frac{df}{dm}=0$.

$$
\frac{df}{dm}=-Jzm-H +k_BT\underbrace{\left[\frac{1}{2}\ln\left(\frac{1+m}{1-m}\right)\right]}_{\tanh^{-1} m}=0\text{.}
$$

We can therefore have the self-consistency equation

$$
m=\tanh\left[\beta(Jzm+H)\right]\text{.}
$$
