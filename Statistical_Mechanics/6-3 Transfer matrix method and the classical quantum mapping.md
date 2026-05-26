# Transfer matrix method and the classical quantum mapping

## The transfer matrix method

Now we are going to solve the one-dimensional Ising model with external field. Now we **change the definition of our notation** to make our discussion more concise.

We define the classical Hamiltonian of the Ising model with periodic boundary condition with $N(\Omega)=N$ spins as as

$$
-\beta H_{\Omega}(\{S_i\})=\underbrace{\beta H}_{\beta}\sum_{i=1}^{N(\Omega)}S_i+\underbrace{\beta J}_{K}\sum_{i=1}^{N(\Omega)}S_iS_{i+1}; J>0\text{.}
$$
Here, $S_{N(\Omega)+1}=S_1$.

The partition function is

$$
Z(h,K,N(\Omega))=Tr\left[e^{h\sum_iS_i+K\sum_iS_iS_{i+1}}\right]\text{.}
$$

Let's start from the simple $h=0$ limit.
When $h=0$, we can define the bond variables $\eta_{i,i+1}\equiv S_iS_{i+1}$. By definition, $\eta_{i,i+1}=\pm1$. Since the bond variables do not couple with each other, the Hamiltonian written in the bond variable is effectively another Ising model but with only magnetic field, $K$. Because of that, the partition function is simply $Z(h=0,K,N(\Omega))=2(2 \cosh K)^{N(\Omega)-1}$.

This approach cannot be generalized to the case with magnetic field $h$. Here we introduce the transfer matrix method and use it to overcome this difficulty.

Let's look at one bond and consider all the possible configurations on this single bond, $(i,i+1)$. Since each bond has two spins coupled together, we can use a matrix to represent the configurations. The row index is corresponds to the spin $i$ and the column index corresponds to the spin $i+1$. Explicitly, we can write down the spin configuration and the corresponding Boltzmann factors as

$$
\left(
\begin{array}{cc}
\uparrow_{i} \uparrow_{i+1} &\uparrow_{i} \downarrow_{i+1}\\
\downarrow_{i} \uparrow_{i+1} & \downarrow_{i} \downarrow_{i+1}
\end{array}
\right)
\xrightarrow{\text{Boltzmann factors}}
\left(
\begin{array}{cc}
e^{K+2h} &e^{-K}\\
e^{-K} & e^{K-2h}
\end{array}
\right)\equiv \widetilde{T}^{(i,i+1)}
$$
Note the $(i,i+1)$ is just the label of the bond not the row/column indices.

In the non-interacting case, we are familiar with the structure that the Boltzmann factor for the full system is just the product of the Boltzmann factors of individual mode since the exponents add up and give us the total energy. Can we do that for our one-dimensional nearest-neighbor coupled systems? Let's take two nearby bonds, $(i-1,i)$ and $(i,i+1)$ and do the matrix product and see what will it lead to. 

Let's focus on the configuration first. Here we use $\boxtimes$ to denote the concept of combine the two configurations to form another configuration. We also use $\boxplus$ to denote the concept of collecting configurations.

$$
\left(
\begin{array}{cc}
\uparrow_{i-1} \underline{\uparrow_{i}} &\uparrow_{i-1} \underline{\underline{\downarrow_{i}}}\\
\downarrow_{i-1} \uparrow_{i} & \downarrow_{i-1} \downarrow_{i}
\end{array}
\right)
\boxtimes
\left(
\begin{array}{cc}
\underline{\uparrow_{i}} \uparrow_{i+1} &\uparrow_{i} \downarrow_{i+1}\\
\underline{\underline{\downarrow_{i}}} \uparrow_{i+1} & \downarrow_{i} \downarrow_{i+1}
\end{array}
\right)\\
=
\left(
\begin{array}{cc}
\uparrow_{i-1} \underline{\uparrow_{i}} \uparrow_{i+1}\boxplus \uparrow_{i-1} \underline{\underline{\downarrow_{i}}} \uparrow_{i+1}
&
\downarrow_{i-1} \uparrow_{i} \uparrow_{i+1}\boxplus \downarrow_{i-1} \downarrow_{i} \uparrow_{i+1}
\\
\uparrow_{i-1} \uparrow_{i} \downarrow_{i+1}\boxplus \uparrow_{i-1} \downarrow_{i} \downarrow_{i+1}
& 
\downarrow_{i-1} \uparrow_{i} \downarrow_{i+1}\boxplus \downarrow_{i-1} \downarrow_{i} \downarrow_{i+1}
\end{array}
\right)
$$

We can see we generate all the $2^3$ configurations for the three spin system by this formal operation.(In fact, the $\boxplus$ notation is just to help understand the structure of the matrix product. The true meaning should corresponds to a rank 3 tensor $T_{S_{i-1},S_i,S_{i+1}}$) How about the Boltzmann's factors?

$$
\widetilde{T}^{(i-1,i)}\widetilde{T}^{(i,i+1)}=
\left(
\begin{array}{cc}
e^{K+2h} &e^{-K}\\
e^{-K} & e^{K-2h}
\end{array}
\right)
\left(
\begin{array}{cc}
e^{K+2h} &e^{-K}\\
e^{-K} & e^{K-2h}
\end{array}
\right)\\
=
\left(
\begin{array}{cc}
e^{K+2h+K+2h}+e^{-K-K} &e^{K+2h-K}+e^{-K+K-2h}\\
e^{-K+K+2h}+e^{K-2h-K} & e^{-K-K}+e^{K-2h+K-2h}
\end{array}
\right)
$$

We can see the representation is very promising. Even thought we are not yet there. All the spin configurations are included. However, the product of the matrix $\widetilde{T}_{i-1,i}\widetilde{T}_{i,i+1}$ does not give the correct Boltzmann factors for the corresponding spin configurations.
For example, the Boltzmann factor for the configuration $\uparrow_{i-1}\uparrow_{i}\uparrow_{i+1}$ should be $e^{2K+3h}$ not $e^{2K+4h}$. If we think through the process, we can immediate realize the discrepancy came from the double counting of energy due to the magnetic field on site $i$.

We immediate discover how to fix our problem. We can consider a system with periodic boundary condition and modify the matrix $\widetilde{T}_{i,i+1}$ as

$$
\widetilde{T}^{(i,i+1)}\to T^{(i,i+1)}=T\equiv
\left(
\begin{array}{cc}
e^{K+h} &e^{-K}\\
e^{-K} & e^{K-h}
\end{array}
\right)=(e^K\cosh h)\textbf{1}+(e^{-K})\sigma_1+(e^{K}\sinh h)\sigma_3\text{.}
$$

The matrix $T$ is the transfer matrix of the Ising model. The representation using Pauli matrices, $\sigma_i$, will be useful for mapping to quantum Hamiltonian later. We can use that to express the partition function as

$$
Z(h,K,N(\Omega))=\sum_{S_1=\uparrow,\downarrow}\sum_{S_2=\uparrow,\downarrow}\cdots\sum_{S_{N(\Omega)}=\uparrow,\downarrow} [T^{(1,2)}]_{S_1,S_2}[T^{(2,3)}]_{S_2,S_3}\cdots[T^{N(\Omega),1}]_{S_{N(\Omega),S_1}}=Tr[T^{N(\Omega)}]\text{.}
$$

The above expression is useful, since we can simplify the calculation significantly by diagonalize $T$. Once $T$ is diagonalized. Let's diagonalize the matrix $T$.

$$
T\xrightarrow{diagonalized}
D=
\left(
\begin{array}{cc}
\lambda_+ &0\\
0 &\lambda_-
\end{array}
\right)\text{.}
$$

Here,

$$
\lambda_{\pm}=e^K\left[\cosh h\pm\sqrt{\sinh ^2 h+e^{-4K}}\right]\text{.}
$$

Let's assume $\lambda_+>\lambda_-$.

We then solve the partition function exactly

$$
Z(h,K,N(\Omega))=\lambda_+^{N(\Omega)}+\lambda_-^{N(\Omega)}=\lambda_+^{N(\Omega)}\left[1+\left(\frac{\lambda_-}{\lambda_+}\right)^{N(\Omega)}\right]\text{.}
$$
When $N(\Omega)\to\infty$, we have

$$
\lim_{N(\Omega)\to\infty} Z(h,K,N(\Omega))\sim \lambda_+^{N(\Omega)}.
$$

The free energy density is

$$
f(h,K)=\lim_{N(\Omega)\to\infty}\frac{F(h,K,N(\Omega))}{N(\Omega)}=-k_BT\ln \lambda_+\\
=-J-k_BT\ln\left[\cosh h\pm\sqrt{\sinh ^2 h+e^{-4K}}\right]\text{.}
$$

At $T>0$, we have the argument in the square root to be positive. So no non-analytic behavior for the free energy density. That is consistent with our previous argument that no finite temperature phase transition in the one-dimensional Ising model.
At $T=0$, we can see the $e^{-4K}$ drops and we have

$$
f(h,K)=-J-k_BT\ln[\cosh h\pm \vert \sinh h\vert]=-J-\vert H\vert \text{.}
$$

As we guessed before, $f(h,K)$ is continuous in $H$ but not smooth in $H$ at $T=0$. Therefore, the magnetization density is $\pm1$ for positive or negative $H$. We can also see this behavior will become smooth once we have the $e^{-4K}$ term.


## The classical quantum mapping

When we stare at the transfer matrix, it seems it is possible to make some connection with the quantum mechanics of a two-level system formally. With this formal interpretation, we define the Hilbert space of the formal system as $|\sigma\rangle=span(|\uparrow\rangle,|\downarrow\rangle)$. The product of the matrices is formally like a time evolution with $\mathcal{i} \Delta t=a$. That is,

$$
|\sigma_{i+1}\rangle=T|\sigma_i\rangle=e^{-a\widehat{H}}\text{.}
$$

It would be interesting to know what $\widehat{H}$ corresponds to. If this formal mapping can be achieved, we find a mapping of our classical statistical mechanics problem to a quantum mechanics system. The sum over classical configurations will correspond to the sum over path, the time evolution, will be a time evolution at imaginary time. To find the corresponding Hamiltonian operator, we need to find the constants $C,c_1,c_2,c_3$ such that

$$
T=C\exp[c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]=\exp[log(C)+c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]\text{.}
$$

Using the fact

$$
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n}&=r^{2n}\\
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n+1}&=r^{2n}(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)\\
r&=\sqrt{c_1^2+c_2^2+c_3^2}\text{,}
$$
we can find

$$
C&=\sqrt{2\sinh 2K}\\
c_2&=0\\
c_3&=c_1 e^{2K}\sinh h
$$

and $c_1$ is the solution of the equation

$$
\tanh\left[c_1\sqrt{1+e^{4K}\sinh^2 h}\right]=\frac{\sqrt{1+e^{4K}\sinh^2 h}}{e^{2K}\cosh h}\text{.}
$$

When $h=0$, the expression simplifies to

$$
C&=\sqrt{2\sinh 2K}\\
c_1&=\tanh^{-1}e^{-2K}\\
c_2&=0\\
c_3&=0\text{.}
$$

Then we have

$$
\widehat{H}=-\frac{1}{a}\left[\frac{1}{2}\log(2\sinh 2K)+c_1\sigma_1\right]\text{.}
$$

We usually drop the constant energy shift and consider the second term only.
The limit $a\to0$ is the so-called **Hamiltonian limit**. If $a\to0$ and we want a well defined $\widehat{H}$ that can be interpret as a Hamiltonian operator, we will require $c_1\sim a\to0$. As $c_1\to0$, $\tanh c_1\sim c_1=e^{-2K}\sim a$ suggest $ae^{2K}$ should be fixed while taking $a\to0$. That is, to get a sensible Hamiltonian operator, we need to take $a\to0$ and $K\to\infty$ simultaneously in a way that $ae^{2K}$ is a constant.

For this Hamiltonian operator to keep the physical property (such as correlation length) invariant while $a\to0$, we need to adjust $K\to\infty$ accordingly. This is the simplest renormalization group equation.(Why?)