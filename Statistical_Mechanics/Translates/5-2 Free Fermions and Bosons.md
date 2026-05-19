# 自由費米子與玻色子

## 量子統計

古典系統與量子系統最重要的差別在於：現在系統的狀態是由波函數描述的。這個差別會帶來什麼新的質性結構？當我們考慮多粒子系統時，波函數的描述會導致一個非常顯著的效果，因為我們不再能夠藉由粒子的「路徑」來區分相同粒子。

所謂相同粒子，是指具有相同內禀性質的粒子，例如質量、電荷、自旋等等。對於古典系統，原則上我們總可以利用路徑追蹤每一顆粒子。然而，當兩個粒子的波函數彼此重疊時，這件事就變得不可能了。困難的來源在於粒子位置的不確定性。

因此，當兩個波函數有可測量的重疊時，這兩個粒子的機率描述就必須不可區分，也就是 $P(\textbf{x}_1,\textbf{x}_2)=P(\textbf{x}_1,\textbf{x}_2)$。由於量子系統的機率與波函數模長平方有關，這會自動導致相應的雙粒子波函數在交換兩粒子後只差一個相位因子，也就是 $\phi(\textbf{x}_1,\textbf{x}_2)=e^{i\theta}\phi(\textbf{x}_2,\textbf{x}_1)$。現在考慮把原波函數中的粒子 1 和粒子 2 交換。立刻可以發現，交換兩次必須回到原本的波函數。因此 $(e^{i \theta})^2=1$，所以 $e^{i\theta}=\pm 1$。對玻色子而言，$e^{i\theta}= +1$；對費米子而言，$e^{i\theta}= -1$。這就是討論量子統計的起點。

由於滿足 $\phi(\textbf{x}_1,\textbf{x}_2)=\pm\phi(\textbf{x}_2,\textbf{x}_1)$，我們可以把波函數分成兩大類：對玻色子而言是對稱化波函數；對費米子而言則是反對稱化波函數。

$$
\phi^{B}(\textbf{x}_1,\textbf{x}_2)=\phi_a(\textbf{x}_1)\phi_b(\textbf{x}_2)+\phi_a(\textbf{x}_2)\phi_b(\textbf{x}_1)\\
\phi^{F}(\textbf{x}_1,\textbf{x}_2)=\phi_a(\textbf{x}_1)\phi_b(\textbf{x}_2)-\phi_a(\textbf{x}_2)\phi_b(\textbf{x}_1)\text{.}
$$

這裡 $a,b$ 是系統的量子數。對費米子來說，若 $a=b$，波函數就會變成零。這就是泡利不相容原理在這個簡單設定中的體現。

例如，光子與聲子是玻色子；電子與中子則是費米子。

```{admonition} 這是什麼？
:class: tip
上面的論證看起來相當一般。不過，在二維空間中會出現一些微妙之處。那裡的交換操作並不那麼平凡，因此除了費米子或玻色子之外，還可能出現不同的量子統計行為。這類粒子稱為 anyon。展示 anyon 物理的一個最簡單模型，是 [toric code model](https://topocondmat.org/index.html)。Anyons 可用於量子計算，因此近年來吸引了大量關注。一些相關主題的近期突破包括 {cite:p}`semeghini2021probing` 與 {cite:p}`satzinger2021realizing`。
```

## 量子多體系統（非交互作用極限）

現在我們知道了有費米子與玻色子。那麼，該如何描述這種量子系統？要定義一個量子系統，我們需要指定哈密頓量 $H$ 與對應的希爾伯特空間 $\mathcal{H}$。這裡我會快速概述具有 $N$ 個粒子的量子多體系統的一般描述方式。

(MHilbertSpace)=
### 希爾伯特空間

先考慮可區分多體系統的波函數。由於粒子彼此可區分，我們可以依此標記希爾伯特空間。總希爾伯特空間為

$$
\mathcal{H}=\mathcal{H}_1\otimes\mathcal{H}_2\otimes\cdots\mathcal{H}_N
$$

此空間中的一個狀態可表示為

$$
\vert \psi)=\vert\phi _{\gamma_1}\}\otimes\vert\phi _{\gamma_2}\}_2\otimes\cdots\vert\phi _{\gamma_N}\}_N\text{.}
$$

這裡 $\vert\phi_{\gamma_i}\}_j$ 是 $\mathcal{H}_j$ 中由量子數 $\gamma_i$ 標記的完備基底。我們用 $\vert \psi\}$ 表示單粒子波函數，用 $\vert \psi )$ 表示尚未考慮不可區分性的多體波函數。這個表達還是有些抽象，因此讓我們從最簡單的非平凡例子開始，一步步建立直覺。

#### 具有兩個粒子的雙能階系統

接下來可以問：在前面那個雙粒子簡單例子中，波函數要如何表示成 ket 向量？只要理解雙粒子時發生了什麼事，就應該知道怎麼推廣到更複雜的情況。

這裡，我們考慮單粒子系統就是一個雙能階系統，也就是 $\gamma_1,\gamma_2\in \{a,b\}$。為了討論所有可能的配置，我們分別考慮 $\gamma_1\neq \gamma_2$ 與 $\gamma_1=\gamma_2$ 兩種情況。

*情況 1*，$\gamma_1\neq \gamma_2$：

$$
\phi^{B/F}(\textbf{x}_1,\textbf{x}_2)&=\sqrt{2}^{-1}\left[\phi_{a}(\textbf{x}_1)\phi_{b}(\textbf{x}_2)\pm \phi_{a}(\textbf{x}_2)\phi_{b}(\textbf{x}_1)\right]=\langle \textbf{x}_1,\textbf{x}_2\vert \phi^{B/F}\rangle\\
\vert \phi^{B/F}_{\{a,b\}}\rangle &= \frac{1}{\sqrt{2}}\left[\vert\phi_{a}\}_1\otimes \vert\phi_{b}\}_2\pm \vert \phi_{b}\}_1\otimes\vert\phi_{a}\}_2 \right]= \frac{1}{\sqrt{2}}\left[\vert\phi_{a}\}_1\otimes \vert\phi_{b}\}_2\pm \vert\phi_{a}\}_2\otimes\vert \phi_{b}\}_1 \right] \text{.}
$$

在最後兩個等號中，我們可以把花括號 ket 理解成：固定希爾伯特空間的順序、去排列量子數 $a,b$；或者反過來，把量子數的順序視為固定，改為排列希爾伯特空間指標。這裡我們用角括號 ket $\vert \phi\rangle$ 來表示已考慮不可區分性的多體波函數。

*情況 2*，$\gamma_1= \gamma_2\in\{a,b\}$：

我們會發現，對費米子系統而言，因為泡利不相容原理，這樣的波函數根本無法形成。不過，玻色子的情況則有兩個可能的態

$$
\vert \phi^B_{\{a,a\}}\rangle &=|\phi_a\}_1|\phi_a\}_2\nonumber\\
\vert \phi^B_{\{b,b\}}\rangle &=|\phi_b\}_1|\phi_b\}_2\text{.}
$$

我們也可以從另一個角度發問：我們到底在做什麼？若兩個希爾伯特空間可區分，則 $\mathcal{H}_1\otimes\mathcal{H}_2$ 的維度是 4。上面的過程，其實是在不可區分性成立時，構造這個空間對應的基底。那麼，費米子希爾伯特空間、玻色子希爾伯特空間與原本的 $\mathcal{H}_1\otimes\mathcal{H}_2$ 之間到底是什麼關係？讓我們透過這個簡單例子來探索其相關結構，再進一步做推廣。

$\mathcal{H}_1\otimes\mathcal{H}_2$ 的四個基底是：

$$
\vert \phi_{ (a,a)}\}&= \vert\phi_a\}_1\vert\phi_a\}_2\nonumber\\
\vert \phi_{ (a,b)}\}&= \vert\phi_a\}_1\vert\phi_b\}_2\nonumber\\
\vert \phi_{ (b,a)}\}&= \vert\phi_b\}_1\vert\phi_a\}_2\nonumber\\
\vert \phi_{ (b,b)}\}&= \vert\phi_b\}_1\vert\phi_b\}_2\text{.}
$$

這裡我們用 $(a,b)$ 來提醒自己，順序是重要的。

現在我們可以問：如何利用費米子或玻色子的基底（已考慮不可區分性，因此順序不重要，我們記作 $\{\gamma_1,\gamma_2\}$）來重建 $\mathcal{H}_1\otimes\mathcal{H}_2$ 的基底？

盯著這些波函數的結構看，我們立刻會意識到 $\mathcal{H}_1\otimes\mathcal{H}_2=\mathcal{H}^B\oplus\mathcal{H}^F$。也就是說，原本那個尚未考慮不可區分性的希爾伯特空間，可以由玻色子希爾伯特空間與費米子希爾伯特空間的直和來組成。換言之，

$$
\vert \phi_{ (a,a)}\}&= \vert \phi^B_{\{a,a\}}\rangle\nonumber\\
\vert \phi_{ (a,b)}\}&= (\vert \phi^B_{\{a,b\}}\rangle+\vert \phi^F_{\{a,b\}}\rangle)/\sqrt{2}\nonumber\\
\vert \phi_{ (b,a)}\}&= (\vert \phi^B_{\{a,b\}}\rangle-\vert \phi^F_{\{a,b\}}\rangle)/\sqrt{2}\nonumber\\
\vert \phi_{ (b,b)}\}&= \vert\phi^B_{\{b,b\}}\rangle\text{.}
$$

所以，我們看清楚了其數學結構。不過，當然我們知道費米子永遠是費米子，因此拿玻色子波函數與費米子波函數做疊加並沒有物理意義。熟悉對稱性如何作用於量子系統的讀者，可能會覺得這種結構和考慮某種對稱性時的不可約表示很相似。這也是為什麼有時我們稱 $\mathcal{H}^B$ 為玻色子 sector，$\mathcal{H}^F$ 為費米子 sector。這些彼此之間不存在疊加原理的 sector，稱為 superselection sector。

#### 一般的費米子與玻色子波函數

把上面的雙粒子簡單波函數，和可區分粒子的波函數相比較，我們就能對一般 $N$ 粒子系統該怎麼做得到一些提示：也就是做對稱求和或反對稱求和。

我們本質上有 $N$ 個粒子，每個粒子都有自己的量子數 $\gamma_i$。從前面的討論我們知道，$\gamma_i$ 是否等於 $\gamma_j$ 會帶來不同的結構。因此，很自然地會想把相同的 $\gamma_i$ 集中起來，讓分析更簡單。進一步來說，我們真正需要的關鍵資訊，是每個 $\gamma_i$ 對應的相同態到底有幾個。所以，與其用量子數表象來表示多體波函數，不如直接用佔據數表象。

佔據數表象的具體定義是

$$
\{\underbrace{\gamma_1,\gamma_2,\cdots ,\gamma_{n_1}}_{n_1\text{ states in } \phi_{\mu=1}}; \underbrace{\gamma_{n_1+1},\gamma_{n_1+2},\cdots,\gamma_{n_1+n_2}}_{n_2 \text{ states in } \phi_{\mu=2}};\cdots;\underbrace{\gamma_{\sum_{\mu=1}^{M-1}n_{\mu}+1},\gamma_{\sum_{\mu=1}^{M-1}n_{\mu}+2},\cdots,\gamma_{\sum_{\mu=1}^{M}n_{\mu}}}_{n_M\text{ states in } \phi_{\mu=M}}\}\text{.}
$$

$N$ 粒子系統的一般化波函數應寫為

$$
\vert \phi^B_N\rangle =\sqrt{\frac{N!}{\prod_{\mu}n_{\mu}!}}^{-1}P_{S}\left[ \vert \phi_{\gamma_1}\}_1 \otimes\vert \phi_{\gamma_2}\}_2 \otimes\cdots\otimes\vert \phi_{\gamma_N}\}_N\right]\\
\vert \phi^F_N\rangle =\sqrt{\frac{N!}{\prod_{\mu}n_{\mu}!}}^{-1}P_{AS}\left[ \vert \phi_{\gamma_1}\}_1 \otimes\vert \phi_{\gamma_2}\}_2 \otimes\cdots\otimes\vert \phi_{\gamma_N}\}_N\right]
$$

其中

$$
P_{S/AS}\left[ \vert \phi_{\gamma_1}\}_1 \otimes\vert \phi_{\gamma_2}\}_2 \otimes\cdots\otimes\vert \phi_{\gamma_N}\}_N\right]&=\sum_p P^{\eta}_p\left[ \vert \phi_{\gamma_1}\}_1 \otimes\vert \phi_{\gamma_2}\}_2 \otimes\cdots\otimes\vert \phi_{\gamma_N}\}_N\right]\nonumber\\
&=\sum_{p}\eta^{\overline{p}}\vert \phi_{\gamma_1}\}_{p(1)} \otimes\vert \phi_{\gamma_2}\}_{p(2)} \otimes\cdots\otimes\vert \phi_{\gamma_N}\}_{p(N)}\text{.}
$$

這裡，$\eta=\pm1$ 分別對應對稱與反對稱求和；$p$ 是 $N$ 個物件的一個排列；$p(j)$ 表示該排列中的第 $j$ 個物件。$\overline{p}$ 則是一個整數，代表要把排列 $p$ 透過交換相鄰元素還原成有序排列所需的步數。舉例來說，對於三個物件的排列 $p=[231]$，有 $\overline{p}=2$，因為我們需要先交換 31，再交換 21，才能回到 $[123]$。總和中包含 $\frac{N!}{\prod_{\mu}n_{\mu}!}$ 項，因此正規化因子是 $\sqrt{\frac{N!}{\prod_{\mu}n_{\mu}!}}^{-1}$。不過，由於泡利不相容原理，在費米子的情況下必須滿足 $n_{\mu}=0/1$；玻色子則沒有這個限制。

從這個構造中，我們也能直接看見泡利不相容原理。當 $\gamma_i=\gamma_j$ 時，所有僅相差交換 $p(i)$ 與 $p(j)$ 的排列對，會相差一個負號。因此這些項會兩兩抵消，最後就導致泡利不相容原理。

我們從簡單情況出發，依照形式上的直觀推導出考慮量子粒子不可區分性後，多體波函數的一般形式。但我們到底在做什麼？本質上，我們是在構造用來描述總希爾伯特空間 $\mathcal{H}$ 的基底，而且特別希望這組基底能滿足量子統計。若要真正確認自己的理解是對的，不妨問自己：最簡單的非平凡例子是什麼？我們能否用它來建立直覺？

```{admonition} 練習
:class: tip
考慮最簡單的非平凡情況：三玻色子系統。
三個粒子的排列有 6 種不同配置。把它們顯式列出如下：

$$
	p_6: (123)\quad 
	p_1: (132)\nonumber\\
	p_2: (231)\quad
	p_3: (213)\nonumber\\
	p_4: (312)\quad
	p_5: (321)\nonumber
$$

根據上面的定義，我們有

$$
	P^{\eta}_{p_2}\left[ \vert\psi_{\alpha}\}_1\otimes\vert\psi_{\beta}\}_2\otimes\vert\psi_{\gamma}\}_3 \right]
	&= \eta^{\overline{p_2}}\left( \vert\psi_{\alpha}\}_{p_2(1)}\otimes\vert\psi_{\beta}\}_{p_2(2)}\otimes\vert\psi_{\gamma}\}_{p_2(3)}\right)\nonumber\\
	&=  \eta^{2}\left( \vert\psi_{\alpha}\}_2\otimes\vert\psi_{\beta}\}_3\otimes\vert\psi_{\gamma}\}_1\right)
$$

在此時，我們先不對 $\alpha,\beta,\gamma$ 做任何限制，將它們視為互不相同，並把三個相同粒子的多體波函數建構為對所有可能排列的總和。事實上，若 $\alpha,\beta,\gamma$ 都彼此不同，我們知道這樣的項總共會有 6 個，因此正規化應該是 $\sqrt{3!}^{-1}$。更具體地說，當 $\alpha\neq\beta\neq\gamma$ 時，

$$
	\vert\phi_{N=3}\rangle& = \frac{1}{\sqrt{6}}
	\Big\{ 
		\left( \vert\psi_{\alpha}\}_1\otimes\vert\psi_{\beta}\}_2\otimes\vert\psi_{\gamma}\}_3\right)+
		\eta\left( \vert\psi_{\alpha}\}_1\otimes\vert\psi_{\beta}\}_3\otimes\vert\psi_{\gamma}\}_2\right)+\nonumber\\
		&\left( \vert\psi_{\alpha}\}_2\otimes\vert\psi_{\beta}\}_3\otimes\vert\psi_{\gamma}\}_1\right)+
		\eta\left( \vert\psi_{\alpha}\}_2\otimes\vert\psi_{\beta}\}_1\otimes\vert\psi_{\gamma}\}_3\right)+\nonumber\\
		&\left( \vert\psi_{\alpha}\}_3\otimes\vert\psi_{\beta}\}_1\otimes\vert\psi_{\gamma}\}_2\right)+
		\eta\left( \vert\psi_{\alpha}\}_3\otimes\vert\psi_{\beta}\}_2\otimes\vert\psi_{\gamma}\}_1\right)
	\Big\}\nonumber\\
	&= \Big\vert\left\{ \alpha,\beta,\gamma \right\}\Big\rangle
$$

接著，假設 $\alpha=\beta=x$。依照同樣的程序，我們有

$$
	P^{\eta}_{p_2}\left[ \vert\psi_{\alpha}\}_1\otimes\vert\psi_{\beta}\}_2\otimes\vert\psi_{\gamma}\}_3 \right]
	&=  \left[ \eta \right]^{2}\left( \vert\psi_{x}\}_2\otimes\vert\psi_{x}\}_3\otimes\vert\psi_{\gamma}\}_1\right)\nonumber\\
	P^{\eta}_{p_5}\left[ \vert\psi_{\alpha}\}_1\otimes\vert\psi_{\beta}\}_2\otimes\vert\psi_{\gamma}\}_3 \right]
	&=  \left[ \eta \right]^{3}\left( \vert\psi_{x}\}_3\otimes\vert\psi_{x}\}_2\otimes\vert\psi_{\gamma}\}_1\right)
$$

若 $\eta=-1$，也就是費米子，這兩項會彼此抵消。我們很容易說服自己，所有項都會如此精確地兩兩抵消。這就是泡利不相容原理。

若 $\eta=+1$，也就是玻色子，這兩項就會相加。不過這裡有個微妙之處：張量積其實是阿貝爾的，因此這兩個基底其實是相同的。於是，不像 $\alpha,\beta,\gamma$ 全都不同時，需要用 6 個基底態來構造具有不可區分性的波函數；當其中兩個量子數相同時，我們其實只需要 3 個基底態就夠了。

更具體地，當 $\alpha=\beta=x,\gamma\neq x$ 時，我們有

$$
	\vert\phi_{N=3}\rangle&= \frac{
		\vert\psi_{x}\}_1\vert\psi_{x}\}_2\vert\psi_{\gamma}\}_3+
		\vert\psi_{x}\}_2\vert\psi_{x}\}_3\vert\psi_{\gamma}\}_1+
		\vert\psi_{x}\}_3\vert\psi_{x}\}_1\vert\psi_{\gamma}\}_2
	}{\sqrt{\frac{3!}{2!1!}}}\nonumber\\
	&= \Big\vert\left\{ x,x,\gamma \right\}\Big\rangle
$$

透過這個顯式表達式，你可以試著交換任意兩個粒子指標，驗證該波函數確實是玻色子／費米子所需的對稱或反對稱波函數。
```

### 多體哈密頓量

$$
H=\sum_i H_i+\underbrace{\sum_{i,j} H_{i,j}+...}_{=0,\text{for non-interacting systems}}\text{.}
$$

當我們把多體哈密頓量 $H$ 對角化後，就會得到多體本徵能譜 $\left\{E_{\gamma}\right\}$ 與多體本徵態 $\left\{\vert E_{\gamma}\rangle\right\}$。

那麼 $\sum_i H_i$ 到底是什麼意思？正確的理解是

$$
H_i=\textbf{1}_1\otimes\textbf{1}_2\otimes\cdots\textbf{1}_{i-1}\otimes H_i\otimes \textbf{1}_{i+1}\cdots \otimes\textbf{1}_N
$$

也就是說，算符 $H_i$ 只在第 $i$ 個粒子的希爾伯特空間上非平凡作用。

假設 ket $\vert \phi_{\gamma'}\rangle_j$ 是哈密頓量 $H_j$ 的本徵態，也就是 $H_j|\phi_{\gamma'}\rangle_j=E_{\gamma'}|\phi_{\gamma'}\rangle_j$。則相應的多體能量本徵態滿足 $H\vert \phi ^{B/F}_N\rangle=\left(\sum_j E_{\gamma_j}\right) \vert \phi^{B/F}_N\rangle=E_{\gamma}\vert \phi^{B/F}_N\rangle$。玻色子與費米子的重大差別就在於泡利不相容原理：玻色子可以全部坐在同一個態上來降低總能量；費米子則必須一個一個疊上去。這就對應到兩個非常重要的概念：玻色-愛因斯坦凝聚，以及費米海。

## 自由費米子與玻色子的配分函數

原則上，在上面多體波函數的表達式中，$\gamma_j$ 可以是任意量子數。例如對自由粒子來說，$\gamma_j$ 可以是動量 $p_j$ 的標記。我們可以說系統中的第 $j$ 個粒子具有動量 $p_j$，然後再像剛剛那樣把整個波函數對稱化／反對稱化。不過，也可以換一種表法來描述系統。既然我們本來就沒有「第 $j$ 個粒子」這種概念，那或許只需要數一數，具有某特定動量 $p_a$ 的粒子有多少個。如此一來，我們就可以用這些數字 $\{n_{p_1},n_{p_2},\cdots, n_{p_a},\cdots\}$ 來描述系統。若這樣做在一個 $N$ 粒子系統中成立，那就必須滿足約束 $\sum_a n_{p_a}=N$。這裡我們用 $a$ 來表示量子數（此處是動量）的索引，與粒子的索引 $j$ 區分開來。

就從這裡開始，用佔據數表象構造帶有內部自由度 $\alpha$ 的量子氣體之正則系綜：

$$
Z_N=\sum_{\alpha}\sum_{\{n_{p_a,\alpha}\}} \delta_{\left(\sum_{\alpha}\sum_a n_{p_a,\alpha}\right),N} \exp\left[-\beta\left(\sum_{\alpha}\sum_{a}\frac{\textbf{p}_a^2}{2m}n_{p_a,\alpha}\right)\right]\text{.}
$$

這個表示法很好，因為它自然納入了量子相同粒子的不可區分性，不再有粒子標記索引了。不過，代價是多出一個由 Kronecker delta 給出的非平凡約束。很自然地，我們會想透過改用巨正則系綜並引入化學勢來鬆開這個限制。於是得到

$$
Z_{GC}=\sum_{N=0}^\infty Z_N e^{\beta \mu N}=\sum_{\alpha}\sum_{\{n_{\textbf{p}_a}\}} \exp\left[-\beta\left(\sum_{\alpha}\sum_{a}\left(\underbrace{\frac{\textbf{p}_a^2}{2m}}_{\epsilon(\textbf{p}_a,\alpha)}-\mu\right)n_{\textbf{p}_a,\alpha}\right)\right]\\
\xrightarrow{\text{factorizable}}\prod_{\alpha} \prod_{\textbf{p}_a} \underbrace{\left[\sum_{n_{\textbf{p}_a}} \exp\left(-\beta (\epsilon(\textbf{p}_a)-\mu) n_{\textbf{p}_a,\alpha}\right)\right]}_{\zeta(\epsilon(\textbf{p}_a,\alpha)-\mu)}\text{.}
$$

這裡我們利用了：對可分離系統而言，配分函數可以因式分解。而且系統能量的具體形式並不重要，我們只是把它一般化寫成 $\epsilon(\textbf{p}_a)$。

對費米子而言，$n_{\textbf{p},\alpha}=0,1$

$$
\zeta(\epsilon(\textbf{p},\alpha)-\mu)=\zeta_F(\epsilon(\textbf{p},\alpha)-\mu)=1+\exp\left[-\beta(\epsilon(\textbf{p},\alpha)-\mu)\right]\text{.}
$$

對玻色子而言，$n_{\textbf{p},\alpha}=0,1,\cdots, \infty$

$$
\zeta(\epsilon(\textbf{p},\alpha)-\mu)=\zeta_B(\epsilon(\textbf{p},\alpha)-\mu)=\frac{1}{1-\exp\left[-\beta(\epsilon(\textbf{p},\alpha)-\mu)\right]}\text{.}
$$

這兩個結果可以合併寫為

$$
\zeta(\epsilon(\textbf{p},\alpha)-\mu)=\zeta_{\eta}(\epsilon(\textbf{p},\alpha)-\mu)=\left(1-\eta\exp\left[-\beta(\epsilon(\textbf{p},\alpha)-\mu)\right]\right)^{-\eta}
$$

其中玻色子／費米子分別對應 $\eta=+1/-1$。如果我們思考一下 $\zeta_{\eta}$ 的意義，就會發現 $\zeta_{\eta}(\epsilon(\textbf{p},\alpha)-\mu)$ 很像是模態 $(\textbf{p},\alpha)$ 自己的巨配分函數。因此，即使我們研究的是多粒子系統，只要藉由轉到巨正則系綜放鬆粒子數約束，就能把每個模態當成彼此獨立來研究其巨配分函數。

從現在開始，我們會使用 $\zeta_{\eta}$ 函數來得到非交互作用費米子與玻色子之巨正則配分函數以及對應熱力學勢的一般表達式。

要繼續往前推，我們先來推導 $\ln Z_{GC}$ 的表達式。立刻可得

$$
-\frac{\Omega}{k_BT}=\ln Z_{GC}=
\sum_{\alpha}\sum_{\textbf{p}_a}\ln \zeta_{\eta}(\epsilon(\textbf{p}_a,\alpha)-\mu)\\
\xrightarrow{\text{對 } \alpha \text{ 做平凡求和}}
(2S+1)\sum_{\textbf{p}_a}\ln \zeta_{\eta}(\epsilon(\textbf{p}_a)-\mu)=(2S+1)\sum_{\textbf{p}_a}\left(-\frac{\Omega_{\textbf{p}_a}}{k_BT}\right)
\text{.}
$$

在最後一行中，如果我們假設能量 $\epsilon(\textbf{p}_a,\alpha)$ 與內部自由度 $\alpha$（例如自旋）無關，那麼對 $\alpha$ 的求和只會帶來一個平凡因子。在簡單情況，例如可分離的費米／玻色氣體中，我們預期這種關係成立，因此 $\sum_{\alpha}\to (2S+1)$。這裡我們假設討論的粒子不是規範粒子，因此內部自由度與自旋 $S$ 有關。（例如自旋 $1/2$ 有兩種可能內部態，即 spin up 與 spin down。事實上，對洛倫茲不變系統而言，存在一個**自旋－統計定理**。這部分留給讀者自行查閱量子場論教材。{cite:p}`srednicki1994chaos`）

一旦取了對數，對 $\textbf{p}_a$ 的乘積就變成求和。於是我們可以進一步問：位於特定動量 $\textbf{p}_a$ 的平均粒子數是多少？這裡再次看見「可分離」假設與使用巨正則系綜的優勢：不同模態基本上是解耦的。因此，當我們要問佔據數的平均值時，只需要計算 $\langle n_{\textbf{p}_a}\rangle= -\frac{\partial \Omega_{\textbf{p}_a}}{\partial \mu}$。也就是

$$
\langle n_{\textbf{p}_a}\rangle= -\frac{\partial \Omega_{\textbf{p}_a}}{\partial \mu}=-\frac{\partial}{\partial \mu} (-\eta)(-\beta)^{-1}\ln(1-\eta e^{\beta(\mu-\epsilon(\textbf{p}_a))})=\frac{e^{\beta(\mu-\epsilon(\textbf{p}_a))}}{1-\eta e^{\beta(\mu-\epsilon(\textbf{p}_a))}}=\frac{1}{e^{\beta(\epsilon(\textbf{p}_a)-\mu)}-\eta}\text{.}
$$

這就是某個態 $\textbf{p}_a$ 上平均會有多少費米子／玻色子佔據。這個函數形式分別稱為費米－狄拉克分佈與玻色－愛因斯坦分佈。在推導這個式子的過程中，我們完全沒有用到能量必須是動量二次函數這件事。因此，只要系統由這組量子數描述，且彼此不互動，這個結果對所有可能量子態都成立。所以我們有更一般的表達式

$$
\langle n_{\gamma}\rangle=\frac{1}{e^{\beta(\epsilon(\gamma)-\mu)}-\eta}
$$

對單粒子態 $\gamma$ 皆成立。這就是著名的費米－狄拉克分佈函數（$\eta=-1$）與玻色－愛因斯坦分佈函數（$\eta=+1$）。

現在來看看，如果把二次動量依賴 $\epsilon(\textbf{p})=\frac{\textbf{p}^2}{2m}$ 與 fugacity $z=e^{\beta \mu}$ 代回去，會發生什麼事。

我們得到

$$
\ln Z_{GC}=(2S+1)\left(\frac{L}{h}\right)^3\int d^3{\textbf{p}} (-\eta) \ln\left[1-\eta z e^{-\frac{\textbf{p}^2}{2mk_BT}}\right]\\
=(2S+1)\left(\frac{L}{h}\right)^3(4\pi)\int_0^{\infty}p^2dp (-\eta) \ln\left[1-\eta z e^{-\frac{\textbf{p}^2}{2mk_BT}}\right]\\
\xrightarrow{p=\sqrt{2mk_BT}\tilde{p}}(2S+1)\left(\frac{L}{h}\right)^3(4\pi)\sqrt{2mk_BT}^3 (-\eta) \int_0^{\infty}\tilde{p}^2d\tilde{p}\ln\left[1-\eta z e^{-\tilde{p}^2}\right]
$$

利用關係式 $\ln(1+x)=-\sum_{n=1}^{\infty} \frac{(-x)^n}{n}$，我們有

$$
\ln Z_{GC}=(2S+1)(4\pi) L^3\sqrt{\frac{2mk_BT}{h^2}}^3 (\eta) \left[\sum_{n=1}^{\infty}\frac{(\eta z)^n }{n}\int_0^{\infty}\tilde{p}^2e^{-n\tilde{p}^2}d\tilde{p}\right]\\
$$

我們注意到，對 $\tilde{p}$ 的積分是高斯積分，因此可以精確計算。這就是來自 $\epsilon(\textbf{p})$ 對動量二次依賴的額外資訊。

$$	
\int_{0}^{\infty} q^2 e^{-nq^2}dq=\frac{1}{2}\left[ -\frac{\partial}{\partial n}\int_{-\infty}^{\infty}e^{-nq^2}dq \right]=\frac{1}{2}\left[ -\frac{\partial}{\partial n} \sqrt{\frac{\pi}{n}}\right]=\frac{1}{2}\frac{1}{2}\sqrt{\pi}n^{-\frac{3}{2}}\text{.}
$$

利用上述結果、自旋－統計定理（$\eta\to(-1)^{2S}$）以及 polylog 函數的定義 $\phi_{\alpha}(z)=\sum_{n=1}^{\infty}\frac{z^n}{n^{\alpha}}$，我們得到

$$
\ln Z_{GC}=\eta (2S+1) \left(\frac{L}{\lambda}\right)^3 \phi_{\frac{5}{2}}(\eta z)
=(-1)^{2S} (2S+1) \left(\frac{L}{\lambda}\right)^3 \phi_{\frac{5}{2}}((-1)^{2S} z)\text{.}
$$

總粒子數的期望值則為

$$
\langle \hat{N}\rangle=N= z\frac{\partial }{\partial z}\ln Z_{GC}= \eta (2S+1) \left(\frac{L}{\lambda}\right)^3 \phi_{\frac{3}{2}}(\eta z)\text{.}
$$

這裡我們用了關係式 $z\frac{\partial}{\partial z} \phi_{\alpha}(cz)=\phi_{\alpha-1}(cz)$。

## 量子氣體的古典極限

當 $z\ll 1$ 時，我們可以近似 $\phi_{\alpha}(\eta z)\sim \eta z$。在這個極限下，可以把 $z$ 寫成 $N$ 的函數，得到

$$
z\approx \frac{1}{2S+1}\frac{N\lambda^3}{L^3}\equiv \frac{1}{2S+1} \xi\text{.}
$$

這裡 $\xi=\frac{\lambda^3}{L^3/N}$ 是一個無因次參數，代表德布羅意熱體積與每個粒子平均佔據體積之比。

這裡可以做一個自洽性檢查：我們先假設 $z\ll1$ 以簡化 $N$ 與 $z$ 的關係，接著得到 $z$ 作為 $\xi$ 的函數。在這個極限下，也可以看出 $\ln Z_{GC}\approx N=\frac{pV}{k_BT}$，這就是古典理想氣體的狀態方程。而我們知道古典極限對應於 $\xi\ll1$。因此，與 $\xi$ 成正比的 $z$ 確實是一個小量。整體是自洽的。

這個推導指出，我們可以用 $\xi$ 來判斷系統是否處在*量子簡併*區域，也就是是否必須考慮量子統計。若 $\xi\ll1$，我們預期量子統計可忽略，系統回到古典極限；當 $\xi\sim \mathcal{O}(1)$ 時，就認為系統進入量子簡併區。

## 簡併費米氣體

現在來思考量子極限，並假設系統由費米子組成。如前所述，泡利不相容原理會在系統的統計行為中扮演重要角色。讓我們拿費米－狄拉克分佈函數來想一想它的意義。當 $\eta=-1$ 時，

$$
n_{F}(\epsilon)=\frac{1}{e^{\beta[\epsilon-\mu]}+1}<1\text{.}
$$

這裡 $\epsilon$ 是被佔據態的單粒子能量。
第一件應注意的事，是這個分佈函數永遠小於 1，這正反映了泡利不相容原理。在低溫極限下，$\beta\to\infty$。此時 $\epsilon-\mu$ 的正負會劇烈改變 $n_F$ 的值。當 $\epsilon>\mu$ 時，$n_F\to0$；當 $\epsilon<\mu$ 時，$n_F\to1$。在 $T=0$ 時，這個閾值 $\mu(T=0)$ 就是費米能 $E_F$，代表被佔據態中的最高能量。對任意溫度，我們有

$$
N=V\int_0^{\infty} dE g(E)n_F(E) \text{.}
$$

這裡 $g(E)$ 是單位體積在能量 $E$ 的態密度。
若令 $T\to0$，便可以很容易對固定粒子數 $N$ 算出費米能。此時

$$
N=V\int_0^{\mu(T=0)=E_F} dE g(E) 
$$

因為此時 $n_F(E)$ 變成階躍函數。態密度的形式取決於系統的哈密頓量。一旦知道這個資訊，就能把費米能寫成粒子數 $N$ 的函數。

費米－狄拉克分佈的一個重要行為，是低溫比熱與溫度呈線性關係。這個結果相當普遍，可以用以下論證理解。

比熱與溫度改變時的能量變化 $\Delta E$ 有關。由於低能態大多已被佔滿，因此當溫度平滑改變時，它們對能量變化幾乎沒有貢獻。所以我們只需要關心接近費米能的那些態。在溫度 $T$ 下，只有能量窗 $\Delta E\approx k_BT$ 內的態會是活躍的。這樣的態數約為 $D(E_F)\Delta E= D(E_F)k_BT$。由於粒子數固定，熱擾動只會把費米子從較低能態激發到較高能態，而能量變化的尺度也是 $k_BT$。因此，對滿足 $E_F\gg k_BT$ 的系統，可近似估計能量變化為 $\delta E=(D(E_F)k_B \delta T)(k_BT)$，從而得到 $C=\frac{\delta E}{\delta T}\propto T$。所以，如果觀察到低溫比熱與溫度呈線性關係，就暗示低能載子可能是形成費米海的費米子，而接近費米面的態對能量傳輸最重要。

若要更詳細計算金屬中的電子，可以把 [Sommerfeld expansion](https://en.wikipedia.org/wiki/Sommerfeld_expansion) 應用到費米－狄拉克分佈上。這部分留給讀者作為練習。

## 簡併玻色氣體

接著來看玻色子的 $\eta=+1$ 情況。

$$
n_{B}(\epsilon)=\frac{1}{e^{\beta[\epsilon-\mu]}-1}\text{.}
$$

這個表達式來自公比為 $e^{-\beta(\epsilon-\mu)}<1$ 的等比級數。假設我們把系統能量最低點選為能量零點，那麼 fugacity 必須滿足 $z=e^{\beta\mu}<1$，也就是 $\mu<0$。

系統總粒子數在 $D$ 維空間中可以寫為

$$
N=(2S+1)\sum_{\textbf{p}_a} n_B(\textbf{p}_a)=(2S+1)\left(\frac{L}{h}\right)^D \int_0^{\infty} S_Dp^{D-1}dp\frac{1}{e^{\frac{p^2}{2mk_BT}}z^{-1}-1}\\
\xrightarrow{p\to\sqrt{2mk_BT} x}
(2S+1)L^D\left(\sqrt{\frac{2\pi mk_BT}{h^2}}\right)^D\frac{2}{\Gamma(D/2)}\underbrace{\int_0^{\infty}ze^{-x^2}\frac{1}{1-ze^{-x^2}} x^{D-1}dx}_{\text{對 }z\text{ 單調遞增的函數}}\\
=(2S+1)\left(\frac{L}{\lambda}\right)^D\frac{2}{\Gamma(D/2)}\sum_{n=1}^{\infty} z^n \underbrace{\int_0^{\infty}x^{D-1} e^{-nx^2}dx}_{\Gamma(D/2)/(2n^{D/2})}\\
=(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(z)<(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(z=1)
$$

這裡，當 $D=2$ 時會對應到黎曼 zeta 函數 $\zeta_R(1)\to\infty$；當 $D=3$ 時，$\zeta_R(3/2)\approx 2.6...$。當 $\phi_{D/2}(1)=C_D$ 有限時，我們就得到一個總粒子數必須滿足的不等式：

$$
N<(2S+1)C_D\left(\frac{L}{\lambda}\right)^{D}
$$

然而我們知道 $\lambda\propto T^{-1/2}$。當 $T\to0$ 時，$\lambda\to\infty$。在某個溫度 $T_c$，這個不等式就會被違反。這怎麼可能？我們的推導哪裡出了問題？
原來，上述論證會在 $n_B(\epsilon)$ 出現奇異行為時失效。當 $\textbf{p}=0$ 時，我們有

$$
n_B(0)=\frac{1}{z^{-1}-1}\text{.}
$$

當我們令 $z\to1$ 以取得 $N$ 的上界時，$\textbf{p}=0$ 上的佔據數會發散。也就是說，把離散求和替換成積分這件事，必須更小心地理解。

一旦觀察到這個行為，我們就知道應該把 $\textbf{p}=0$ 模態與其餘 $\textbf{p}\neq0$ 模態分開處理。對於 $\textbf{p}\neq0$ 的模態，積分近似仍然沒有問題。因此，佔據在 $\textbf{p}=0$ 模態上的粒子數可寫為

$$
N_{\textbf{p}=0}=N-N_{\textbf{p}\neq0}=N-(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(z)>N-(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(1)\\
=N\left[1-\underbrace{(2S+1)\frac{1}{N}\left(\frac{L\sqrt{2\pi m k_B}}{h}\right)^D\phi_{D/2}(1)}_{T_c^{-D/2}} T^{D/2}\right]=N\left[1-\left(\frac{T}{T_c}\right)^{D/2}\right]
$$

另一方面，fugacity $z$ 是由 $\textbf{p}\neq0$ 模態上的粒子數決定的，也就是

$$
N_{\textbf{p}\neq0}=(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(z)<(2S+1)\left(\frac{L}{\lambda}\right)^D\phi_{D/2}(1)\equiv N_{\textbf{p}\neq0}^M\text{.}
$$

當 $N<N_{\textbf{p}\neq0}^M$ 時，一切都沒問題，因為我們總能在 $\textbf{p}\neq0$ 的態中找到地方放玻色子，並相應調整 $z$。若在固定溫度下持續往系統中加入更多玻色子，$z$ 就會開始上升並趨近於 1。當粒子數達到某個臨界值後，我們已無法再把更多玻色子放進 $\textbf{p}\neq0$ 的態中，因為那些態已經被「填滿」了。此時唯一能放玻色子的地方，就是 $\textbf{p}=0$。
根據玻色－愛因斯坦分佈，我們有 $N_0=\frac{1}{z^-1-1}$，因此可解出 $z=\frac{N_0}{N_0+1}$。當玻色子被放進 $\textbf{p}=0$ 時，$N_0$ 變大，而 $z$ 會更接近 1。當 $N_0$ 很大時，可見 $z$ 近似為 $z\approx 1-N_0^{-1}$。
