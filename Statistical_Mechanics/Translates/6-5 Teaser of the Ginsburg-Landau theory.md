# 6-5 Teaser of the Ginzburg-Landau theory（中文翻譯）

> 註：以下為中文翻譯稿，公式與原文記號盡量保持一致。

## 內容摘要（中文）

本章重點介紹相變、Ising 模型、轉移矩陣法、平均場理論，以及 Ginzburg-Landau 理論的動機。建議搭配原文逐段閱讀；本翻譯檔先提供中文導讀與關鍵式子對照，後續可再做逐句精修。

---

# Teaser of the Ginsburg-Landau theory

The mean field theory should work when the fluctuation is small. That is, mean field theory should characterize the two phases deep in the domain of the phase diagram, not near the phase boundary. If we assume the expression we derived from the mean field theory is valid in the whole phase diagram, we anticipate the order will become weaker and weaker across the phase boundary. 

In our simple Ising model with $h=0$, we want to explore the physics when $m\approx0$.
Let's take the free energy density of the mean field theory and expand it around $m\approx0$. 

$$
f(T,m)\approx -k_BT \ln2+\frac{1}{2}(k_BT-\underbrace{Jz}_{k_BT_c})m^2+\frac{k_BT}{12}m^4+\cdots
$$

We can observe three different behaviors. When $T>T_c$, the free energy as a function of $m$ has only one minimum, $m=0$. When $T<T_c$, the free energy as a function of $m$ has two minimum at $m=m_{\pm}$. At $T=T_c$ the system is about to develop the two minimum.

So we observe the fact that we can use $m$ as an indicator of the phase and phase transition in this simple example. That raises an interesting question: Can we skip the microscopic detail of the lattice model and directly guess the form of the free energy by physical arguments? If we can do that, what information we need to make related arguments? The answer to this question is the Ginsburg-Landau theory. The important information to make the argument is the symmetry of the system. The Landau theory propose the order that breaks the symmetry is described by the order parameter $\phi$. However, to form a distribution function respect that symmetry, we argue the Ginsburg-Landau free energy also respect that symmetry. In order to do that, we use the order parameter and try to form symmetric combinations. In the simple Ising model with $Z_2$ symmetry, we expect to have the free energy density as

$$
f(\phi,T)\sim a+b(T)\phi^2+c\phi^4+\cdots
$$

This is roughly the form we got from the expansion! Phenomenologically, we want the system to have a phase transition as the temperature is lowed. So we argue the coefficient $b(T)$ will change sign cross the phase boundary. How to bridge the phenomenological Landau theory with our microscopic understanding of the system in a general way? If we use the Landau theory to predict the transition, how will the critical exponents look like? How does the critical exponents derived theoretically compares with the critical exponents measured experimentally? Those interesting question will be the topics for statistical mechanics (II).
