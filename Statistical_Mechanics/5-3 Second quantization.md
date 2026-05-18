# Second quantization

## Qualitative difference between non-interacting quantum many-particle system and the interacting many-body system: Why second quantization?

To deal with quantum many-body systems, it is important to keep the structure of its quantum statistics. *i.e.* whether the system is formed by fermions or bosons. In the previous section, we work in the basis that forming the partition function and related calculations are almost trivial. 

The reason that the related calculation is trivial is because we work in the eigen basis of the system. However, it is usually very challenging to get the eigen basis for the many-body quantum systems. Let's try to understand the qualitative difference between the non-interacting many-particle systems and the interacting many-body systems.

We can start from the simplest quantum system: a system formed by quantum bits (two-level system). The dimension of the Hilbert space for a quantum bit is 2. This is the simplest non-trivial case where we can have the non-trivial structure due to the superposition principle. (If there is only one basis in the space, we cannot show the superposition structure). Let's use $\mathcal{H}_b$ to represent the Hilbert space of the quantum bit. To be more specific, we can assign the two basis in the Hilbert space to be $\left\{ |\uparrow\rangle,|\downarrow\rangle \right\}$. The most general state in this space is given by $c_{\uparrow}|\uparrow\rangle+c_{\downarrow}|\downarrow\rangle$.

Now, let's consider the non-interacting quantum many-particle system. In our simple example above, we have lots of quantum bits that does not talk with each other. So to understand the system, essentially all we need to do is to understand what a single quantum bit is doing. So even though we have many particles (in this case, many quantum bits), the problem is essentially a one-body problem. So the eigen specturm of the system is simple, all we need to do is to diagonalize the $2\times2$ matrix. The full spectrum will simple accumulation of the 2 eigne energies for the $2\times2$ Hamiltonian.

Next, we can try to see what happened if we start to couple the quantum bits. When the quantum bits start to talk with each other, the system will be described by a state in the Hilbert space formed by the tensor product of individual Hilbert space for each quantum bit. That is, $\mathcal{H}=\otimes_{j=1}^{N_s}\mathcal{H}_{b,j}$. This is a space that the dimensionality grows exponentially as a function of the system size (in this case, the number of quantum bits, $N_s$).

Now we can see the qualitative difference. In the non-interacting case, we need to diagonalize a $2\times 2$ matrix. We know how to do that. For the interacting case, we need to diagonalize a $2^{N_s}\times 2^{N_s}$ matrix. Which you can try to run that on your computer by choosing $N_s=10,20,40$. Usual desktop can get the full spectrum of the $N_s=10$ case easily, $N_s=20$ and $N_s=40$ case is beyond the ability for the usual desktop. That's why we call such problem a *many-body* problem, because we need to consider the system as a whole and cannot factorize our system and reduce the problem to a one-body problem.

Of course, we are not going to stop there. We will try to see if we can still make some progress to understand the many-body problem. Now we have several choices:

* Start from the non-interacting limit and try to develop some kind of perturbation theory.
* Using some non-perturbative methods, such as mean-field theory or variational method to get the relevant states of our problem. We will introduce the idea of mean field theory which is a versatile method for interacting problem. 
 
Here, we will introduce a notation, *second quantization*, which is convenient to develop a perturbation analysis for the quantum many-body system. We have learned the single particle perturbation theory in quantum mechanics. The challenge here is how to develop the corresponding theory when we consider the quantum statistics(fermions or bosons) of our problem. To do that, we need to find a convenient representation for the many-body wave function and the many-body Hamiltonian. That representation is the *second quantization* formulation that we are going to introduce.

Note that, the formal expression of second quantization looks pretty much like what you will learned in the quantum field theory. Second quantization is essentially an expression of quantum mechanics but just with many particles. However, in quantum field theory, usually there are other structures such as Lorentz invariance. So, make sure you know what you are doing!

## The many-body states and operators in the second quantization representation

### Review of the occupation number representation

We have briefly discussed the many-body Hilbert space {ref}`MHilbertSpace`. The key concept here is the occupation number representation of the wave function. Let's review our notation briefly here.

1. $|\{n_{u}\}\rangle$ with $\sum_u n_u=N$: We use $|\rangle$ to denote the many-particle wave function with quantum statistics considered. Here, $\{n_u\}$ is the corresponding occupation number of the state.
2. $|u_i\}$: We use $|\}$ to denote the single particle wave function, no information about quantum statistics.
3. The corresponding many-particle wave function is

$$
|\phi_N\rangle=\sqrt{\frac{\prod_{u}n_u!}{N!}}\sum_{p_{u}} P_{p_{u}}^{\eta}\left[|u_1,u_2,\cdots,u_{n_1};u_{n_1+1},u_{n_1+2},\cdots,u_{n_1+n_2};\cdots\}\right]\text{.}
$$
Here we define

* $p_{u}$: permutation of $N$ objects with $n_u$ identical objects $|u\}$. The number of such permutation is $\frac{N!}{\prod n_u!}$.
* $\eta$: $\eta=\pm1$ for Bosons/Fermions
* $P_{p_{u}}^{\eta}\left[\quad\right]$: symmetrize or anti-symmetrize the single particle states with the corresponding phase factor.
	* $\overline{p_{u}}$: The number of nearest neighbor swapping to go from $p_{u}$ to the reference permutation, $\{1,2,3,...\}$.
	* $P^{\eta}_{p_{u}}\left[|u_1\}_1|u_2\}_2\cdots|u_{m}\}_{m}...\right]=\eta^{\overline{p_{u}}}|u_1\}_{p_{u}(1)}|u_2\}_{p_{u}(2)}\cdots|u_{m}\}_{p_{u}(m)}...$. When $\eta=-1$ for fermion, this corresponds to the so called *Slater determinant*.

### The many-particle operators

#### The $N_p$ particle operator

An operator that at least requires $N_p$ single particle wave functions to determine its matrix element is considered as an $N_p$ particle operator. (Trivial addition does not count)

Or, we can say $N_p$-particle operators are operators that act non-trivially on $N_p$ single-particle Hilbert space.

**examples**

* 1-particle operator:
	* kinetic energy: given a single particle state $|q\}$, we can evaluate the matrix element $\{q|\frac{\widehat{P}^2}{2m}|q\}$.
	* Zeeman field: given a spin state $|\uparrow\rangle$, we can evaluate the matrix element $\{\uparrow|B_z\widehat{S_z}|\uparrow\}$.
* 2-particle operator:
	* Coulomb interaction: Usually we use $\widehat{H}_c=V(\widehat{r_1}-\widehat{r_2})$ to express the Coulomb interaction. Given $|r_1\}$ and $|r_2\}$, we can evaluate the matrix element $_1\{r_1|_2\{r_2|V(\widehat{r_1}-\widehat{r_2})|r_1\}_1|r_2\}_2$.
	* exchange energy: It describes how two quantum spins are coupled. Usually we have $\widehat{H}_J=-J\widehat{S}_1\cdot\widehat{S}_2$. Given $|\uparrow\}_1|\uparrow\}_2$, we can evaluate the matrix element $\{\uparrow|\{\uparrow|\widehat{H}_J|\uparrow\}|\uparrow\}$.

	
To learn how to express the many-body operators using the many-body basis, we start from the simplest non-trivial case: bosonic one-particle operator.
	
### The second quantization representation of an one-particle operator for bosons

Let's use the following notation to define the 1-particle operator for $N$ bosons. We have the definition of the 1-particle operator. Basically, we have all the matrix elements for the operator. That is, we have $_j\{\alpha|\widehat{O}^{(I)}_j|\beta\}_j$. For simplicity, we will drop the index $j$ to represent the generic matrix element for single-particle operator, $\{\alpha|\widehat{O}^{(I)}|\beta\}$.

$$
\widehat{O}^{(I)}_{total}&=\sum_{j=1}^N\widehat{O}^{(I)}_j \\
&=\left(\sum_{\phi_N}|\phi_N\rangle\langle \phi_N|\right)\sum_{j=1}^N\widehat{O}^{(I)}_j\left(\sum_{\phi_N'}|\phi_N'\rangle\langle \phi_N'|\right)
$$

The goal is to express the sum of the one-particle operator via the many-body wave function. To do that, we need to evaluate the matrix element $\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi_N'\rangle$. 

Let's try to imagine what we are facing. $|\phi_N\rangle$ is the symmetric sum of the single particle wave function. Therefore, we have $\frac{N!}{\prod_{u}n_{u}!}$ terms in $|\phi_N\rangle$. Similarly, for $|\phi_N'\rangle$, we have $\frac{N!}{\prod_{v}n_{v}!}$. Also, we have the $\sum_{j=1}^N$ for the operator $\widehat{O}^{(I)}_j$. So we have lots of terms. It appears that it is hopeless for use to evaluate the matrix element. Luckily, lots of the terms are zero.

We need to express the many-particle states using the single-particle states since that's how we connect to the matrix element for the single-particle operator.

The generic term that appears in sum that express the matrix element $\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi_N'\rangle$ is

$$
&\left(_{p_{\alpha}(1)}\{u_1|_{p_{\alpha}(2)}\{u_2|\cdots\right)\widehat{O}^{(I)}_j\left(|v_1\}_{p_{\beta}(1)}|v_2\}_{p_{\beta}(2)}\cdots\right)\\
&=\cdots\underbrace{_{p_{\alpha}(i)}\{u_i|O^{(I)}_j|v_k\}_{p_{\beta}(k)}}_{p_{\alpha}(i)=p_{\beta}(k)=j}\cdots \overbrace{\underbrace{_{p_{\alpha}(\tilde{i})}\{u_{\tilde{i}}|v_{\tilde{k}}\}_{p_{\beta}(\tilde{k})}}_{p_{\alpha}(\tilde{i})=p_{\beta}(\tilde{k})\neq j}}^{\delta_{u_{\tilde{i}},v_{\tilde{k}}}}\cdots \text{.}
$$
Here, we explicitly show two possible terms when we evaluate the matrix element.
Since the generic term in the $\sum_{p_{\alpha}}\sum_{p_{\beta}}\sum_j$ is expressed using single particle states. Therefore, we need to pick the inner product in the same single particle Hilbert space. There are two possibilities, either we pick the $j$-th Hilbert space where $\widehat{O}^{(I)}_j$ acts non-trivially or we pick other Hilbert spaces where we only need to take care of the inner product of two single particle states. Since the single-particle wave functions are orthonormal, the later case will give us a Kronecker delta function to make sure the single particle quantum number at that single particle Hilbert space to be identical.

Let's pulse and think about what's the meaning of the above expression. Let's consider the cases when the two sets of quantum numbers $\{u_i\}$ and $\{v_i\}$ are
1. identical
2. different by one quantum number
3. different by two quantum numbers or more

Starting from the simplest case when the two sets of quantum numbers are identical, $\{u_i\}=\{v_i\}$. For each permutation $p_{\alpha}$, we expect to find a $p_{\beta}$ such that all the quantum number are arranged in the correct way such that the inner product in each Hilbert space is $1$ and the full product is identical with the diagonal matrix element of the $j$-th operator $\widehat{O}^{(I)}_j$.

In the second case, we have one quantum number that is different. To have non-zero contribution, we need to arrange the correct permutation as we discussed in the first case, but also, we need to put the different quantum numbers in the $j$-th Hilbert space such that it is evaluating the off-diagonal matrix element of $\widehat{O}^{(I)}_j$ which will not be 0 in general. The reason is simple, if we don't do that, the different quantum numbers need to do inner product at other single particle Hilbert space which will inevitably give us 0.

Now it should be obvious that for one-particle operator, if the two sets of quantum numbers differ by more than one quantum number, the result will always be 0. Since we can put one of the distinct pair in the $j$-th Hilbert space to evaluate the off-diagonal matrix element of $\widehat{O}^{(I)}_j$. But the next pair of distinct quantum numbers will do the inner product in other single-particle Hilbert space and gives us 0!

That's a huge simplification, we only need to care about the first two situation. So let's put things down in a more precise mathematical expression.

#### The matrix element for an one-particle operator for bosons

* When $\{u_i\}=\{v_i\}$, we should have

$$
&\sum_{p_{u}}\sum_{p_{v}}\sum_{j=1}^N\cdots _{p_{u}(i)}\{u_i|\widehat{O}^{(I)}_j|v_k\}_{p_{v}(k)}\cdots \delta_{u_{\tilde{i}},v_{\tilde{k}};p_{u}(\tilde{i})=p_{v}(\tilde{k})}\cdots \\
&=\underbrace{\frac{N!}{\prod_{u}(n_{u}!)}}_{\sum_{p_{u}},\sum_{p_{v}=p_{u}}}\underbrace{\left(\sqrt{\frac{\prod_{u} (n_{u}!)}{N!}}\right)^2}_{\text{normalization from }\langle \phi_N|,|\phi'_N\rangle}\sum_{j=1}^N \{u_i|\widehat{O}_j^{(I)}|u_i\}_{p_u(i)=j} \\
&=\sum_{\alpha} \{\alpha|\widehat{O}^{(I)}|\alpha\} n_{\alpha}
$$

Notice here $p_{\beta}$ is chosen such that the quantum number $\{v_i\}$ is identical with $\{u_i\}$. Also, in the last equality, we switch from the single particle representation to the occupation number representation.

* When $\{u_i\}=\{v_i\}$ except when $i=i^*$. Now we should be careful, let's use $\alpha,\beta$ to label the quantum number $u_{i^*}=\alpha,v_{i^*}=\beta$. When we switch to occupation number representation, we should have

$$
\{u_i\}&\to \{\cdots,n_{\alpha},\cdots,n_{\beta},\cdots\}\\
\{v_i\}&\to \{\cdots,n_{\alpha}-1,\cdots,n_{\beta}+1,\cdots\}
$$

Here, we use the occupation number of $\{u_i\}$ as the reference.

$$
&\sum_{p_{u}}\sum_{p_{v}}\sum_{j=1}^N\cdots _{p_{u}(i)}\{u_i|\widehat{O}^{(I)}_j|v_k\}_{p_{v}(k)}\cdots \delta_{u_{\tilde{i}},v_{\tilde{k}};p_{u}(\tilde{i})=p_{v}(\tilde{k})}\cdots \\
&=\underbrace{\frac{N!\overbrace{n_{\alpha}}^{\beta \text{ can be attached with arbitrary }\alpha}}{\prod_{u}(n_{u}!)}}_{\sum_{p_{u}}\sum_{p_{v}}}\times \underbrace{\left(\sqrt{\frac{\prod_{u} (n_{u}!)}{N!}}\right)}_{\text{normalization from }\langle \phi_N|}\underbrace{\left(\sqrt{\frac{\prod_{v\neq\alpha,\beta} (n_{v}!)}{N!}}\sqrt{(n_{\alpha}-1)!(n_{\beta}+1)!}\right)}_{\text{normalization from }|\phi'_N\rangle}\times\\
&\sum_{j=1}^N \{u_{i^*}|\widehat{O}_j^{(I)}|v_{i^*}\}_{p_u(i^*)=p_v(i^*)} \\
&=\sqrt{n_{\alpha}(n_{\beta}+1)} \{\alpha|\widehat{O}^{(I)}|\beta\}
$$

In the last equality, we use the fact that for each permutation, only when $j=p_u(i^*)=p_v(i^*)$ will give non-zero matrix element.

Recall that $\widehat{O}^{(I)}$ is hermitian, so we should also have the hermitian conjugate matrix element with similar structure. We can simply perform the hermitian conjugate of the operator. This operation corresponds to $u\leftrightarrow v$, which is equivalent to $\alpha\leftrightarrow \beta$. 
The corresponding matrix element is 

$$
\sqrt{n_{\beta}(n_{\alpha}+1)} \{\beta|\widehat{O}^{(I)}|\alpha\}\text{.}
$$

* Now we should see why the rest of the terms are zero! When $u_{i^*}=\alpha_1\neq v_{i^*}=\beta_1$ and $u_{j^*}=\alpha_2\neq v_{j^*}=\beta_2$, we will have terms like

$$
\cdots \{u_{i^*}|\widehat{O}_j^{(I)}|v_{i^*}\}_{p_u(i^*)=p_v(i^*)}\cdots\{u_{j^*}|v_{j^*}\}_{p_u(j^*)=p_v(j^*)}\cdots=0\text{.}
$$

To sum up, 

$$
\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi'_N\rangle=
\left\{
\begin{array}{c}
\sum_{\alpha}(\widehat{O})_{\alpha,\alpha}n_{\alpha}\\
\sum_{\alpha\neq \beta}(\widehat{O})_{\alpha,\beta}\sqrt{n_{\alpha}(n_{\beta}+1)}
\end{array}
\right.
$$

We went through the long derivation and understand that even though the permutation gives us lots of combinations, most of the terms are zero. The next question is: can we have a concise way to systematically express the many-particle operator and states such that we can do the book keeping process more efficiently? That's what we are going to show in the next section. We will introduce the idea of creation and destruction operators. We can see shortly why they are convenient tools to represent the many-particle operators. The representation of many-particle operators using the creation/destruction operators is the **second quantization**.

#### The bosonic creation/destruction operators

The bosonic creation/destruction operators, $b^{\dagger}_k/b_k$ are defined as

$$
\begin{array}{c}
&[b_k,b_{k'}^{\dagger}]=\delta_{k,k'}\\
&[b_k,b_{k'}]=[b_k^{\dagger},b_{k'}^{\dagger}]=0
\end{array}
\text{.}
$$

Here $k,k'$ are single particle quantum numbers. $[A,B]=AB-BA$ is the commutator.
The simplest Hermitian object we can form is

$$
\widehat{n}_k=b_k^{\dagger}b_k\text{.}
$$

At this moment, we don't know what is $\widehat{n}_k$. However, we do know it is Hermitian and diagonalizable. So we can assign the eigen states of $\widehat{n}_k$ as $|n_k\rangle$ with

$$
\widehat{n}_k|n_k\rangle=n_k|n_k\rangle\text{.}
$$

The eigen value $n_k\ge0$ since

$$
n_k=\langle n_k|\widehat{n}_k|n_k\rangle=\sum_m\langle n_k|b_k^{\dagger}|m\rangle\langle m|b_k|n_k\rangle=\sum_m |\langle m|b_k|n_k\rangle|^2\ge0\text{.}
$$

Next, we can ask what's the effect of $b_k$ when it is applied to $|n_k\rangle$. We can notice

$$
[\widehat{n}_k,b_k]=-b_k
$$

When apply this relation to $|n_k\rangle$, we have

$$
\widehat{n}_k(b_k|n_k\rangle)=(n_k-1)(b_k|n_k\rangle)
$$

So, $b_k$ lower the quantum number by 1.
From this observation, the possible values of $n_k$ is fixed to be non-zero integers. If they are not, we can always have some $n_k<0$ which violates our previous proof. If $n_k$ is integer, it will stop at $n_k=0$.

Once we know this fact, we can construct the action of $b_k$ on $|n_k\rangle$ explicitly.

Assume $b_k|n_k\rangle=c_1|n_k-1\rangle$

$$
n_k=\langle n_k|b_k^{\dagger}b_k|n_k\rangle=\langle n_k|c_1^*c_1|n_k-1\rangle=|c_1|^2
$$
So we know $c_1=\sqrt{n_k}e^{i\phi_1}$. Here the phase can be gauged away and we can have

$$
b_k|n_k\rangle=\sqrt{n_k}|n_k-1\rangle\text{.}
$$

Using the commutator relation, we can also show

$$
b_k^{\dagger}|n_k\rangle=\sqrt{n_k+1}|n_k+1\rangle\text{.}
$$

Using the bosonic creation/destruction operator, we can easily represent the operator $\widehat{O}^{(I)}_{total}$ in the occupation basis as

$$
\widehat{O}^{(I)}_{total}=\sum_{\alpha,\beta} b_{\alpha}^{\dagger} [\widehat{O}^{(I)}]_{\alpha,\beta} b_{\beta}\text{.}
$$

We can show that the above mentioned matrix element can be derived by

$$
[\widehat{O}^{(I)}_{total}]_{\{n_u\},\{n_v\}}=\langle \{n_u\}|\sum_{\alpha,\beta} b_{\alpha}^{\dagger} [\widehat{O}^{(I)}]_{\alpha,\beta} b_{\beta}|\{n_v\}\rangle \text{.}
$$

#### Bosonic Hamiltonian in second quantization representation

Here, we construct the representation for one-particle operator. The construction for bosonic two-particle operator can be found in {cite:p}`fetter2012quantum`. It will be left as an exercise.

### What is left...

1. Second quantization for fermions: to construct the second quantized expression of fermions, one needs to take care of the phase factor carefully. Therefore, we need to introduce fermionic creation/destruction operators.

	$$
	[f_k,f^{\dagger}_{k'}]_+&=\delta_{k,k'}\\
	[f_k,f_{k'}]+&=[f^{\dagger}_k,f^{\dagger}_{k'}]_+=0
	$$
2. A concise treatment of the problem can be found in {cite:p}`feynman2018statistical`.
3. Perturbation theory using second quantization: Basically, that's related to the Feynman diagram and is beyond the scope of the current course.
4. Other quantum mechanical techniques can be reformulated in second quantization language. *e.g.* variational method, mean field theory, etc.
5. In general, the second quantized Hamiltonian looks like

$$
\widehat{H}=\sum_{i,j}a_i^{\dagger}\{i|\widehat{T}|j\}a_j+\frac{1}{2}\sum_{i,j,k,l}a_i^{\dagger}a_j^{\dagger}\{ij|\widehat{V}|kl\}a_la_k \text{.}
$$

Here, $a_k$ can be bosonic or fermionic operators. $\widehat{T}$ is the one-particle operators such as kinetic energy. $\widehat{V}$ is the two-particle operators such as Coulomb interaction.