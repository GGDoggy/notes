# Phonon and photon

We are going to discuss the statistical mechanics for phonon and photon. Here, we will brief discuss the origin of phonon and photon. The discussion will just focus on the physics and the relevant formalism to derive statistical mechanics descriptions. For readers who want to review details of the derivation, we will refer to the nice reference {cite:p}`simon2013oxford`.

## Phonon

Phonons are the quantum of sound wave. Therefore, in order to understand it, we need to have a rough picture of sound wave in solid. To get the core concept, we will focus on the simplest type of phonon: phonon in simple lattice system.

### The phonon band structure

Symmetries usually help us simplify the analysis the problems. The lattice system has a *discrete* translational symmetry. How to use this symmetry to simplify the analysis of our problem? 

In a system with *continuous* translation symmetry, the momentum is conserved. So we usually use momentum to label the eigen states of our system.

For system with *discrete* translation symmetry, we can similarly use the crystal momentum vector $\textbf{k}$ to label the eigen states.

Let's start from the simple one-dimensional system. The system contains two length scale. 
1. From the discrete translation symmetry with lattice constant $a$. *i.e.* $H(x)=H(x+a)$ (Physics constraint!).
2. Usually, we consider the periodic boundary condition. *i.e.* $H(x)=H(x+L)$(Convenient choice of boundary condition!). For later convenience, we assume we have $N$ sites, so $L=Na$.

We also know, the *continuous* translation symmetry system has eigen state $e^{ipx/\hbar}=e^{ikx}$. The *discrete* translation symmetry is a subset of the *continuous* translation symmetry. *i.e.* we only consider the ones that are invariant under shift of $a$ and $L=Na$. This naturally leads to two characteristic crystal momentum vectors.
1. $e^{iGa}=1$, $G=G_0 m$ where $G_0=\frac{2\pi}{a}$ and $m\in\mathcal{Z}$. $G_0$ form the reciprocal lattice in the reciprocal space.
2. $e^{iqL}=1$, $q=q_0 n$ where $q_0=\frac{2\pi}{L}=\frac{1}{N}G_0$ and $n\in\mathcal{Z}$. $q$ are the wave vectors in the reciprocal space. Usually, when $L\to\infty$, we have $q_0\to0$. The energies corresponds to each $q$ in the reciprocal space will form a band. Depends on the nature of the excitation, it could be a band of phonon, which we will discuss later, or a band of electron.

The key difference between the system with *continuous* and *discrete* translation symmetry is the conservation law. For system with *continuous* translation symmetry, we have momentum conservation. For system with *discrete* translation symmetry, we have *quasimomentum* (or *crystal momentum*) conservation. The *quasimomentum* conservation means the wave vector $q$ is well defined up to integer multiples of $G_0$. *i.e.* $q\equiv q+G_0$. Why it is so? it is related to the fact that the discrete representations of continuous wave for wave with wave vector $q$ and $q+G_0$ are indistinguishable. The phenomena is called *wave aliasing*. See the [wikipedia link](https://en.wikipedia.org/wiki/Crystal_momentum) and the [wikipedia gif](https://en.wikipedia.org/wiki/Crystal_momentum#/media/File:Quasimomentum.gif).

Because of the quasimomentum conservation, we usually focus our description for $q\in(-G_0/2,G_0/2]$. This region is called the first Brillouin zone.

Usually, when we open the textbook of solid state physics, we will see two phonon bands in the first Brillouin zone. The branch that is gapless with $\lim_{|q|\to0}E(q)\propto |q|$ is the acoustic phonon. The branch that is gapped is the optical phonon.

In the last section, we discussed $N$ decoupled quantum harmonic oscillator. They can be considered as a good approximation to the optical phonon if the gapped modes are approximately $q$ independent. In fact, that is the Einstein's phonon model{cite:p}`einstein1907plancksche`. 

### Classical 1D sound wave

Here, we are going to discuss a simple example which is an one-dimensional coupled oscillators. The example is a model that is analytically tractable. However, as all the simple models, we should care about the generic feature of such systems instead of focusing on the artifact due to its simplicity. I will explain what do I mean by that later.

We will focus on the classical system first. Then we can derive the energy as a function of $q$. Then, we will take the short cut to perform the classical-quantum replacement $E(q)=\hbar\omega(q)\to\hbar\omega(q)\left(\frac{1}{2}+\hat{n}_q\right)$. Here $\hat{n}_q$ is the quanta of a quantum oscillator with wave vector $q$.

Let's start our analysis. Consider $N$ particles with mass $m$ coupled through spring with elastic potential $\frac{\kappa}{2}\Delta x^2$. Here $\kappa$ is the force constant and $\Delta x$ is the displacement from the equilibrium position. We assume the equilibrium position of the particles form a lattice with lattice constant $a$.

The total potential energy of the system is

$$
V_{\text{total}}(\left\{x_i\right\})=\sum_i V(x_{i+1}-x_i)\approx\sum_i\frac{\kappa}{2}\left(x_{i+1}-x_i-a\right)^2=\sum_i\frac{\kappa}{2}\left(\delta x_{i+1}-\delta x_i\right)^2\text{.}
$$
Here, $\delta x_i=x_i-x_{i,eq}$.

The total force applied on the $n$-th particle is

$$
F_n=-\frac{\partial V_{\text{total}}(\left\{x_i\right\})}{\partial x_n}=m\frac{\partial ^2 \delta x_n}{\partial t^2} = \kappa\left[\left(\delta x_{\text{n+1}}-\delta x_{n}\right)-\left(\delta x_n-\delta x_{n+1}\right)\right]\text{.}
$$

If we use the ansatz, $\delta x_n=A e^{i\omega t-iqx_{n,eq}}$, to solve these equations, we have

$$
m\omega^2=2\kappa(1-\cos qa);\omega(q)=2\sqrt{\frac{\kappa}{m}}\vert\sin\frac{qa}{2}\vert\text{.}
$$

The simple function form of $\omega(q)=2\sqrt{\frac{\kappa}{m}}\vert\sin\frac{qa}{2}\vert$ is not generic. The generic structure is the fact that $\lim_{q\to0}\omega(q)\approx vq$. The linear dispersive mode is related to the Goldstone theorem. When a continuous symmetry is spontaneously broken, a linear dispersive mode emerges. In this case, the continuous symmetry is the continuous translation symmetry. After the symmetry is spontaneously broken, we have our phonon model. 

For a quantized system, we have a quantum harmonic oscillator with frequency $\omega(q)$ for each mode $q$. Also, the phonon mode has polarization. For 3D isotropic system, the polarization is 3. We will use $\alpha$ to label the polarization of each mode.

In general we should have partition function expressed as

$$
Z=\sum_{\left\{n_{q,\alpha}\right\}} \exp\left[-\beta \sum_{q,\alpha} \hbar\omega_{\alpha}(q)\left(\frac{1}{2}+n_{q,\alpha}\right)\right]\xrightarrow{\text{factorize}}\prod_{q,\alpha}\left\{\sum_{n_{q,\alpha}}\exp\left[-\beta \hbar\omega_{\alpha}(q)\left(\frac{1}{2}+n_{q,\alpha}\right)\right]\right\}\text{.}
$$

To focus on the point, we assume the dispersion is isotropic and replace the discrete sum by integral in the later discussion.

### Debye model

As we mentioned previously, $\omega(q)$ depends on the system detail. The generic feature due to the Goldstone theorem is $\omega(q)\sim vq$ as $q\to0$. Another constraint is the classical limit of the quantum model should leads to specific heat $3Nk_B$ for a 3D system. To incorporate the two generic feature into one model, Debye propose to linearize the whole spectrum and put in a frequency cutoff by hand. Let's see how it is done.

1. The linear dispersive mode: Let's assume $\omega(q)=vq$ and $dq=v^{-1}d\omega$. Then we have the energy expectation value described as 

	$$
	\langle \hat{H}\rangle=E\approx 3(4\pi)\left(\frac{L}{2\pi v}\right)^3\int_0^\infty \omega^2 d\omega \exp\left[-\beta \hbar\omega(q)\left(\frac{1}{2}+\langle \hat{n}_q\rangle\right)\right]\\
=\int_0^{\infty}d\omega g(\omega)\hbar\omega(\frac{1}{2}+n_B(\beta\hbar\omega))
	$$
	Here $g(\omega)$ is the density of states that represents the number of states in the energy window $[\omega,\omega+d\omega]$ including the polarization. $n_B(\beta\hbar\omega)=\frac{1}{e^{\beta\hbar\omega}-1}$.
	After some algebra, we found
	
	$$
	g(\omega)=N\frac{9\omega^2}{\omega_d^3};\omega_d^3=6\pi^2\frac{N}{L^3}v^3\text{.}
	$$
	We can change the variable of the integral using dimensionless parameter $x=\beta\hbar\omega$. After that, we have
	
	$$
	\langle \hat{H}\rangle=\frac{9N\hbar}{\omega_d^3} (\beta \hbar)^{-4}\underbrace{\int_0^{\infty} dx\frac{x^3}{e^x-1}}_{\pi^4/15}+\text{temperature independent constant.}
	$$
	Then we can get the specific heat for bosonic linear dispersive mode to be
	
	$$
	C=\frac{\partial E}{\partial T}\propto T^3
	$$
   
1. The frequency cutoff: The $T^3$ behavior of specific heat is tied with the linear dispersive mode. If that behavior is not changed, the behavior will extend to $T\to\infty$ limit. Of course, it is not the classical behavior that we anticipate. How to fix that? Debye fix that by cutoff the frequency integral at a value $\omega_{cutoff}$ such that the total number of modes below the cutoff frequency to be exactly $3N$, the total number of modes in this system. *i.e.*
	
	$$
	\int_0^{\infty}d\omega\to\int_0^{\omega_{cutoff}} d\omega=3N\text{.}
	$$
	
	With this cutoff, we have the energy expectation value as
	
	$$
	\langle \hat{H}\rangle=\int_0^{\omega_{cutoff}}d\omega g(\omega)\hbar\omega(\frac{1}{2}+n_B(\beta\hbar\omega))\xrightarrow{\beta\hbar\omega\to0}\int_0^{\omega_{cutoff}}d\omega g(\omega)\hbar\omega(\beta\hbar\omega)^{-1}\approx 3Nk_BT\text{.}
	$$
	And we recover the classical limit $C\to 3Nk_BT$.

## Photon

The calculation of phonon is very similar with the photon case. Here I just list some of the key difference and the derivation will be left as an exercise.

1. Completely linear dispersive mode.
2. The magnitude of the velocity is the speed of light.
3. Polarization of photon is two due to its gauge nature. In three-dimensional space, we have the polarization number of photon to be 2.