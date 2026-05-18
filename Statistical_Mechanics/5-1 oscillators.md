# Oscillators

We are dealing with free systems so far. The ideal gas ( free particles) and the paramagnetic phase of spins ( free binary variables). Now we can try to explore the situation when the particles are interacting free, but experience an external potential. The most important case is the oscillators.

## Classical 1D oscillators at temperature $T$

Let's follow the flow chart in the last section to study the system.

<style>
table th:first-of-type {
    width: 10%;
}
table th:nth-of-type(2) {
    width: 30%;
}
table th:nth-of-type(3) {
    width: 60%;
}
</style>

| Stage  | Statistical mechanics idea                                                                                                              | The physical system                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :----: | :-----------------:                                                                                                                     | :---------------:                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 1      | Pick a system                                                                                                                           | A bunch of independent classical oscillators                                                                                                                                                                                                                                                                                                                                                                                                            |
| 2      | Identify the relevant microscopic degrees of freedom, $\xi$                                                                             | The coordinate and momentum of the oscillator, $(R_i,P_i)$.                                                                                                                                                                                                                                                                                                                                                                                             |
| 3      | Construct the possible energy for the microscopic degree of freedom.                                                                    | In this case, the Hamiltonian is given, so we don't need to worry about how to write down the corresponding Hamiltonian. Basically, $H=\sum_{i=1}^N H_i$. $H_i=\frac{P_i^2}{2m}+\frac{\kappa}{2}R_i^2$.                                                                                                                                                                                                                                                 |
| 4      | Now we can pick an ensemble that satisfied the constraint of our system. We pick the canonical ensemble since temperature $T$ is fixed. | Most of the time, the experiments study the equilibrium system with fixed temperature. Therefore, we usually pick the canonical ensemble. Then, according to our previous knowledge of statistical mechanics. We know how to construct the partition function. For our system case, $Z=\int \left(\prod_{i=1}^N\frac{dR_idP_i}{h}\right) \exp\left[-\beta \sum_{j=1}^N \frac{1}{2m}P_j^2+\frac{m\omega_0^2}{2}R_j^2\right]$ with $\omega_0^2=\kappa/m$. |
| 5      | We can improved our guess of $\xi$ and $H(\xi)$ by comparing with experiments. (Going back to stage 2.)                                 | Since the Hamiltonian is given in this problem, there is no need to compare with experiments.                                                                                                                                                                                                                                                                                                                                                           |

The potential obstacle 1 does not exist, since the problem is a pedagogical problem. The potential obstacle 2 is whether we can evaluate the partition function.

$$
Z\xrightarrow{\text{interacting free}} \prod_{i=1}^{N}\left[\int \frac{dR_idP_i}{h} \exp\left[-\left(\frac{\beta}{2m}\right) P_i^2\right]\exp\left[-\left(\frac{\beta m\omega_0^2}{2}\right) R_i^2\right]\right]=\left(\frac{1}{\beta \hbar\omega_0}\right)^N\text{.}
$$

The most important structure for interacting free system is the total energy is the sum of individual degree of freedom. That property automatically leads to a factorizable partition function. Therefore, the partition function of the system is the product of partition functions for individual degree of freedom. I will leave this integral as an exercise since it is simply the Gaussian integral for momentum and coordinate.

The energy expectation value of the system and the specific heat are

$$
\langle H\rangle=E=\frac{\partial \ln Z}{\partial (-\beta)} =Nk_BT; C=\frac{\partial E}{\partial T}=Nk_B\text{.}
$$

We can observe two very important structure:
1. The result is independent of $\omega_0$.
2. The Gaussian integral in momentum and space contribute $\frac{k_BT}{2}$ each to the specific heat.

### The equi-partition theorem

Suppose the Hamiltonian of our system can be approximated by

$$
H=H_0(X_1,X_2,\cdots,X_r)+ H_1(X_{r+1},\cdots, X_N)\text{.}
$$

Here $H_0$ is the part of the energy that is quadratic in its arguments. Because of that, we have

$$
\sum_{i=1}^r X_i\frac{\partial H_0}{\partial X_i}=2H_0\text{.}
$$

Here, we focus on the effect given by $H_0$. The expectation value of the energy from $H_0$ is

$$
\langle H_0\rangle =\frac{1}{Z}\int \left(\prod_{i=1}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \underbrace{H_0(X_1,\cdots, X_r)}_{\frac{1}{2}\sum_{l=1}^r X_l\frac{\partial H_0}{\partial X_l}} \exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\text{.}
$$

Now we can notice

$$
X_l\frac{\partial }{\partial X_l}\left[\exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\right]\\
=X_l(-\beta \frac{\partial }{\partial X_l}H_0(X_1,\cdots,X_r))\exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\text{.}
$$

Using this identity, we have

$$
\langle H_0\rangle =\frac{-k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)} \\
=\frac{-k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1,i\neq l}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \int dX_l X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)}
\text{.}
$$
Here we suppressed the argument of $H_0$ and $H_1$ to make our notation more concise. We also focus on the integral over $X_l$ first.

$$
\int dX_l X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)}=\underbrace{\left. X_l e^{-\beta(H_0+H_1)}\right|_{-\infty}^{\infty}}_{=0, \because \left.e^{-\beta H_0}\right|_{\pm\infty}\to0}-\int dX_le^{-\beta(H_0+H_1)}
$$

Therefore, we can simplify the expression as

$$
\langle H_0\rangle 
=\frac{k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1,i\neq l}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \int dX_l e^{-\beta(H_0+H_1)}=\frac{k_BT}{2} \frac{1}{Z} (rZ)= r\frac{k_BT}{2} 
\text{.}
$$
So we can see each quadratic mode contribute energy expectation value $\frac{k_BT}{2}$. The simple harmonic oscillator and the ideal gas are the special case for this theorem.

* ideal gas model: energy is quadratic in momentum. In 3D, each particle contribute $3\times \frac{k_BT}{2}$. $N$ particle system therefore has internal energy $\frac{3Nk_BT}{2}$.
* Oscillators: energy is quadratic in momentum and coordinate. In 1D, each oscillator contribute $2\times \frac{k_BT}{2}$. $N$ 1D oscillators has internal energy $Nk_BT$.

## Quantum Harmonic oscillators

We will perform similar procedure to analyze the system.


<style>
table th:first-of-type {
    width: 10%;
}
table th:nth-of-type(2) {
    width: 30%;
}
table th:nth-of-type(3) {
    width: 60%;
}
</style>

| Stage |                                                       Statistical mechanics idea                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 The physical system                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| :---: | :-------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|   1   |                                                              Pick a system                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     A bunch of independent quantum oscillators                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|   2   |                                       Identify the relevant microscopic degrees of freedom, $\xi$                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    The wave function $\vert \phi_{n}^{(i)}\rangle$ for each oscillator for $i=1\sim N$ with energy $E_n=\left(n+\frac{1}{2}\right)\hbar \omega$.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|   3   |                                  Construct the possible energy for the microscopic degree of freedom.                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            In this case, the Hamiltonian is given, so we don't need to worry about how to write down the corresponding Hamiltonian. Basically, $\hat{H}=\sum_{i=1}^N \hat{H}_i$. $\hat{H}_i=\frac{\hat{P}_i^2}{2m}+\frac{\kappa}{2}\hat{R}_i^2=\left(\hat{n}_i+\frac{1}{2}\right)\hbar\omega$. Here, the position, momentum, and Hamiltonian are promoted into quantum operators. Here $[X_i,P_i]=i\hbar$ and $\omega=\frac{\kappa}{m}$.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|   4   | Now we can pick an ensemble that satisfied the constraint of our system. We pick the canonical ensemble since temperature $T$ is fixed. | Most of the time, the experiments study the equilibrium system with fixed temperature. Therefore, we usually pick the canonical ensemble. Then, according to our previous knowledge of statistical mechanics. We know how to construct the partition function. For our system case, $Z=\sum_{n_1=0}^{\infty}\sum_{n_2=0}^{\infty}\cdots \sum_{n_N=0}^{\infty}\exp\left[-\beta\left(\sum_{j=1}^{N}\left(n_j+\frac{1}{2}\right)\hbar\omega\right)\right]$. Because the system is interacting free, the partition function is factorizable. We have $Z=\zeta^N$. Here $\zeta=\sum_{n=0}^{\infty}\exp\left[-\beta\left(n+\frac{1}{2}\right)\hbar\omega\right]=\frac{e^{\frac{-\beta \hbar\omega}{2}}}{1-e^{-\beta\hbar\omega}}$. In the last equality, we explicitly calculate $\zeta$ since it is a geometric series that we can derived explicitly. Once we have the partition function, we can follow the standard process to get the energy $E=\frac{\partial \ln Z}{\partial (-\beta)}=N\hbar\omega\left(\frac{1}{2}+n_B(\beta \hbar\omega)\right)=N\hbar\omega\left(\frac{1}{2}+\frac{1}{e^{\beta\hbar\omega}-1}\right)$ and $C=\frac{\partial E}{\partial T}=Nk_B\left[(\beta\hbar\omega)^2\frac{e^{\beta\hbar\omega}}{(e^{\beta\hbar\omega}-1)^2}\right]$. The specific heat goes to $Nk_B$ when $\beta\hbar\omega\to0$; at the $\beta\hbar\omega\to\infty$ limit, the quantum nature of the system suppresses the specific heat exponentially. |
|   5   |                 We can improved our guess of $\xi$ and $H(\xi)$ by comparing with experiments. (Going back to stage 2.)                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            Since the Hamiltonian is given in this problem, there is no need to compare with experiments.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |



```{admonition} What?
:class: tip
What is the meaning of partition function of a quantum system?
It seems like we are doing the calculation on a classical system. The only difference is the energy is quantized.  

In a classical system, we said we have a microscopic configuration, $\xi$, which has probability proportional with $e^{-\beta H(\xi)}$. *i.e.* We have an ensemble of microscopic configurations and the probability distribution of the ensemble is assigned accordingly.

In a quantum system, we said we have an eigen state, $\vert E_n\rangle$, which has probability proportional with $e^{-\beta E_n}$. *i.e.* We have an collection of states in our ensemble with the classical probability distribution proportional with $e^{-\beta E_n}$. Readers with a keen eye on the derivation might ask: where is the information of wave function? The partition function is suppose to help us evaluate the expectation value of the system. When we evaluate the mean value of an observable in quantum mechanics, shouldn't we evaluate something like $\langle \psi\vert \hat{O}\vert\psi\rangle$? That is correct! The reason we can avoid this complication is because the observable we choose here is the Hamiltonian and the quantum mechanics expectation value for the states, $\vert E_n\rangle$, in the ensemble give $\langle E_n\vert \hat{H}\vert E_n\rangle=E_n$. This information is already included in the partition function. If we want to evaluate the center of mass of the system, we need to evaluate $\hat{O}=\sum_i \hat{x}_i$, then, we will need to evalate $\langle E_n\vert \sum_i\hat{x}_i\vert E_n\rangle$ which is the piece of information that is not contained in the partition function.

That is, the general definition of an ensemble of a quantum system requires two pieces of informaiton. One is the classical probability for the collection of states, the other is the corresponding wave function. In statistical mechanics, we got the classical probability using the Boltzmann factor. In genral, one needs to define the system via the density matrix. The density matrix in the energy representation is 

$$
\hat{\rho}=\sum_{E_n} P(E_n)\vert E_n\rangle\langle E_n\vert=\sum_{E_n} \frac{\vert E_n\rangle e^{-\beta E_n}\langle E_n\vert}{Z}=\frac{e^{-\beta \hat{H}}}{Z}\sum_{E_n} \vert E_n\rangle \langle E_n\vert=\frac{e^{-\beta \hat{H}}}{Tr\left[e^{-\beta \hat{H}}\right]}\text{.}
$$

The expectation value of an observable $\hat{O}$ is

$$
\langle \hat{O}\rangle=\sum_{E_n} P(E_n)\langle E_n\vert\hat{O}\vert E_n\rangle=Tr\left[\hat{\rho} \hat{O}\right]\text{.}
$$

We can see there are two kinds of "average" for the expectation value. One is from the statistical average over $P(E_n)$. The other is from the quantum average done by the $\langle E_n\vert\hat{O}\vert E_n\rangle$. When we choose to evaluate the expectation value of the Hamiltonian, the quantum average becomes trivial. That's why our evaluation of energy expectation value looks pretty "classical".

One interesting question is: are there qualitative difference when we try to move from classical statistical mechanics to quantum statistical mechanics? It turns out the Newton's second law and the Schödinger equation has an intrinsic difference. The Newton's equation could have nonlinear effect easily. However, Schödinger equation is a linear equation. That suggest the notion of chaos needs to be rethought in quantum systems. Currently, it is a research subject on how a close quantum system reaches thermal equailibrium. Readers can check the reference {cite:p}`nandkishore2014many` for more information.
```


## Key points to learn from the two example

The two examples demonstrate several important ideas:
1. How to construct partition functions when the energy is quantized or continuous? Integral and summation!
2. The partition function is factorizable because the systems are interacting free. The origin of this property is the total energy for interacting free systems can be derived by simply summing the energy of individual parts.