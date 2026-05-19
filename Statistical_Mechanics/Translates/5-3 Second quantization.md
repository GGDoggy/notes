# 第二量子化

## 非交互作用量子多粒子系統與交互作用多體系統的質性差異：為什麼需要第二量子化？

要處理量子多體系統，保留其量子統計的結構是很重要的，也就是系統究竟由費米子還是玻色子組成。在上一節中，我們使用的基底讓配分函數與相關計算幾乎變得微不足道。

之所以相關計算如此簡單，是因為我們工作在系統的本徵基底中。然而，對量子多體系統而言，要找出本徵基底通常極具挑戰性。讓我們試著理解非交互作用多粒子系統與交互作用多體系統之間的質性差異。

我們可以從最簡單的量子系統開始：由量子位元（雙能階系統）組成的系統。量子位元的希爾伯特空間維度是 2。這是最簡單的非平凡例子，因為在這裡疊加原理才會產生非平凡結構。（若空間裡只有一個基底，就無法展現疊加結構。）我們用 $\mathcal{H}_b$ 表示量子位元的希爾伯特空間。更具體地說，我們可以把這個空間中的兩個基底取為 $\left\{ |\uparrow\rangle,|\downarrow\rangle \right\}$。這個空間中最一般的態可寫為 $c_{\uparrow}|\uparrow\rangle+c_{\downarrow}|\downarrow\rangle$。

現在來考慮非交互作用的量子多粒子系統。在上面的簡單例子中，我們有許多彼此不互相作用的量子位元。因此，要理解整個系統，本質上只需要理解單一量子位元在做什麼。也就是說，雖然我們有很多粒子（在這裡是很多量子位元），但問題本質上仍是一體問題。所以系統的本徵譜很簡單，我們只需要對一個 $2\times2$ 矩陣對角化即可。完整的能譜只不過是這個 $2\times2$ 哈密頓量兩個本徵能量的累積。

接著，我們可以看看當量子位元彼此耦合之後會發生什麼事。當量子位元開始互相「對話」時，系統將由每個量子位元各自希爾伯特空間的張量積所描述，也就是 $\mathcal{H}=\otimes_{j=1}^{N_s}\mathcal{H}_{b,j}$。這個空間的維度會隨系統大小（在這裡是量子位元數目 $N_s$）呈指數成長。

現在我們就能看出質性的差別。在非交互作用的情況下，我們只需要對角化一個 $2\times 2$ 矩陣，這件事我們很熟悉。但在交互作用的情況下，我們需要對角化一個 $2^{N_s}\times 2^{N_s}$ 的矩陣。你可以試著在電腦上取 $N_s=10,20,40$ 來實驗看看。一般桌機很容易算出 $N_s=10$ 的完整能譜，但 $N_s=20$ 或 $N_s=40$ 通常就超出一般桌機的能力範圍了。這也是為什麼我們把這類問題稱為*多體*問題，因為我們必須把系統作為整體來看待，無法再把系統拆開並還原成一體問題。

當然，我們不會就此止步。我們仍要嘗試看看，是否能對多體問題做出一些進展。現在我們有幾個選擇：

* 從非交互作用極限出發，發展某種擾動理論。
* 使用某些非擾動方法，例如平均場理論或變分法，來找出與問題相關的重要態。我們之後會介紹平均場理論，它是一種處理交互作用問題的通用方法。
 
這裡我們要介紹一種記號，叫做*第二量子化*。它對發展量子多體系統的擾動分析非常方便。我們在量子力學中已經學過單粒子擾動理論。現在的挑戰是，當問題涉及量子統計（費米子或玻色子）時，要如何發展對應的理論。為了做到這點，我們需要找到一種方便的表示方式來描述多體波函數與多體哈密頓量。這種表示方式就是接下來要介紹的*第二量子化*形式。

注意，第二量子化的正式表達式看起來和量子場論中的東西很像。第二量子化本質上仍然是量子力學，只是處理的是多粒子系統。然而，在量子場論中，通常還會有其他結構，例如洛倫茲不變性。所以，請務必清楚自己在做什麼。

## 第二量子化表象中的多體態與算符

### 佔據數表象回顧

我們已經簡短討論過多體希爾伯特空間 {ref}`MHilbertSpace`。這裡的關鍵概念是波函數的佔據數表象。現在簡要回顧一下我們的記號。

1. $|\{n_{u}\}\rangle$ 且 $\sum_u n_u=N$：我們用 $|\rangle$ 表示已經納入量子統計的多粒子波函數。這裡的 $\{n_u\}$ 是對應的佔據數。
2. $|u_i\}$：我們用 $|\}$ 表示單粒子波函數，其中不包含量子統計資訊。
3. 對應的多粒子波函數為

$$
|\phi_N\rangle=\sqrt{\frac{\prod_{u}n_u!}{N!}}\sum_{p_{u}} P_{p_{u}}^{\eta}\left[|u_1,u_2,\cdots,u_{n_1};u_{n_1+1},u_{n_1+n_2};\cdots\}\right]\text{.}
$$

其中我們定義

* $p_{u}$：$N$ 個物件的排列，其中有 $n_u$ 個彼此相同的物件 $|u\}$。這種排列的總數是 $\frac{N!}{\prod n_u!}$。
* $\eta$：對玻色子與費米子分別取 $\eta=\pm1$。
* $P_{p_{u}}^{\eta}\left[\quad\right]$：對單粒子態做對稱化或反對稱化，並帶上對應的相位因子。
	* $\overline{p_{u}}$：從排列 $p_u$ 回到參考排列 $\{1,2,3,...\}$ 所需的最近鄰交換次數。
	* $P^{\eta}_{p_{u}}\left[|u_1\}_1|u_2\}_2\cdots|u_{m}\}_{m}...\right]=\eta^{\overline{p_{u}}}|u_1\}_{p_{u}(1)}|u_2\}_{p_{u}(2)}\cdots|u_{m}\}_{p_{u}(m)}...$。當費米子取 $\eta=-1$ 時，這對應到所謂的 *Slater determinant*。

### 多粒子算符

#### $N_p$ 粒子算符

若某個算符至少需要 $N_p$ 個單粒子波函數，才能決定其矩陣元素，那它就被視為一個 $N_p$ 粒子算符。（平凡的相加不算）

或者，我們也可以說，$N_p$ 粒子算符是在 $N_p$ 個單粒子希爾伯特空間上非平凡作用的算符。

**例子**

* 1 粒子算符：
	* 動能：給定單粒子態 $|q\}$，我們可以計算矩陣元素 $\{q|\frac{\widehat{P}^2}{2m}|q\}$。
	* Zeeman 場：給定自旋態 $|\uparrow\rangle$，我們可以計算矩陣元素 $\{\uparrow|B_z\widehat{S_z}|\uparrow\}$。
* 2 粒子算符：
	* 庫侖交互作用：通常我們用 $\widehat{H}_c=V(\widehat{r_1}-\widehat{r_2})$ 來表示庫侖交互作用。給定 $|r_1\}$ 與 $|r_2\}$，我們可以計算矩陣元素 $_1\{r_1|_2\{r_2|V(\widehat{r_1}-\widehat{r_2})|r_1\}_1|r_2\}_2$。
	* 交換能：它描述兩個量子自旋如何耦合。通常寫成 $\widehat{H}_J=-J\widehat{S}_1\cdot\widehat{S}_2$。給定 $|\uparrow\}_1|\uparrow\}_2$，我們可以計算矩陣元素 $\{\uparrow|\{\uparrow|\widehat{H}_J|\uparrow\}|\uparrow\}$。

要學會如何用多體基底表示多體算符，我們從最簡單的非平凡情況開始：玻色子的一粒子算符。

### 玻色子一粒子算符的第二量子化表示

讓我們用下面的記號來定義 $N$ 個玻色子的一粒子算符。我們已經有一粒子算符的定義；基本上，我們已經知道這個算符所有的矩陣元素，也就是 $_j\{\alpha|\widehat{O}^{(I)}_j|\beta\}_j$。為了簡單起見，我們省略指標 $j$，用 $\{\alpha|\widehat{O}^{(I)}|\beta\}$ 表示單粒子算符的一般矩陣元素。

$$
\widehat{O}^{(I)}_{total}&=\sum_{j=1}^N\widehat{O}^{(I)}_j \\
&=\left(\sum_{\phi_N}|\phi_N\rangle\langle \phi_N|\right)\sum_{j=1}^N\widehat{O}^{(I)}_j\left(\sum_{\phi_N'}|\phi_N'\rangle\langle \phi_N'|\right)
$$

我們的目標，是把這個一粒子算符的總和用多體波函數表達出來。為了做到這點，我們需要計算矩陣元素 $\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi_N'\rangle$。

讓我們先想像一下自己面對的是什麼。$|\phi_N\rangle$ 是單粒子波函數的對稱和，因此它裡面有 $\frac{N!}{\prod_{u}n_{u}!}$ 項。類似地，$|\phi_N'\rangle$ 裡面有 $\frac{N!}{\prod_{v}n_{v}!}$ 項。此外，算符部分還有 $\sum_{j=1}^N \widehat{O}^{(I)}_j$。所以整體看起來會有非常多項，乍看之下幾乎不可能算完。幸運的是，其中大多數項其實都等於零。

我們需要把多粒子態展開成單粒子態，因為只有這樣才能接上單粒子算符的矩陣元素。

在表示矩陣元素 $\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi_N'\rangle$ 的總和中，會出現的一般項為

$$
&\left(_{p_{\alpha}(1)}\{u_1|_{p_{\alpha}(2)}\{u_2|\cdots\right)\widehat{O}^{(I)}_j\left(|v_1\}_{p_{\beta}(1)}|v_2\}_{p_{\beta}(2)}\cdots\right)\\
&=\cdots\underbrace{_{p_{\alpha}(i)}\{u_i|O^{(I)}_j|v_k\}_{p_{\beta}(k)}}_{p_{\alpha}(i)=p_{\beta}(k)=j}\cdots \overbrace{\underbrace{_{p_{\alpha}(\tilde{i})}\{u_{\tilde{i}}|v_{\tilde{k}}\}_{p_{\beta}(\tilde{k})}}_{p_{\alpha}(\tilde{i})=p_{\beta}(\tilde{k})\neq j}}^{\delta_{u_{\tilde{i}},v_{\tilde{k}}}}\cdots \text{.}
$$

這裡我們明確寫出了在計算矩陣元素時可能出現的兩類項。由於 $\sum_{p_{\alpha}}\sum_{p_{\beta}}\sum_j$ 中的一般項是以單粒子態寫成，因此我們必須在同一個單粒子希爾伯特空間中取內積。這裡有兩種可能：要嘛取的是第 $j$ 個希爾伯特空間，也就是 $\widehat{O}^{(I)}_j$ 非平凡作用的那個空間；要嘛取的是其他希爾伯特空間，此時我們只需要處理兩個單粒子態的內積。由於單粒子波函數彼此正交歸一，後者會產生 Kronecker delta，要求該單粒子希爾伯特空間中的量子數必須相同。

現在暫停一下，想想上面的式子到底代表什麼。考慮兩組量子數 $\{u_i\}$ 與 $\{v_i\}$ 有以下三種情況：
1. 完全相同
2. 只差一個量子數
3. 差兩個或兩個以上量子數

先從最簡單的情況開始，也就是兩組量子數完全相同：$\{u_i\}=\{v_i\}$。對每個排列 $p_{\alpha}$，我們都預期可以找到一個 $p_{\beta}$，讓所有量子數都以正確方式對上，因此每個希爾伯特空間中的內積都等於 1，最後整體乘積就等於第 $j$ 個算符 $\widehat{O}^{(I)}_j$ 的對角矩陣元素。

第二種情況是只有一個量子數不同。若要有非零貢獻，我們除了要像第一種情況那樣安排出正確的排列外，還必須把不同的量子數放在第 $j$ 個希爾伯特空間中，這樣計算到的才會是 $\widehat{O}^{(I)}_j$ 的非對角矩陣元素，而它一般不會是零。原因很簡單：如果不這麼做，那對不同量子數的內積就會落在其他單粒子希爾伯特空間裡，結果必然是 0。

現在應該很明顯了：對一粒子算符而言，如果兩組量子數差超過一個量子數，結果一定為 0。你可以把其中一對不同量子數放進第 $j$ 個希爾伯特空間，用來計算 $\widehat{O}^{(I)}_j$ 的非對角矩陣元素；但接下來另一對不同的量子數就只能在其他單粒子希爾伯特空間做內積，結果會直接給出 0。

這是一個巨大的簡化，我們只需要考慮前兩種情況。現在把事情寫得更精確一些。

#### 玻色子一粒子算符的矩陣元素

* 當 $\{u_i\}=\{v_i\}$ 時，我們應有

$$
&\sum_{p_{u}}\sum_{p_{v}}\sum_{j=1}^N\cdots _{p_{u}(i)}\{u_i|\widehat{O}^{(I)}_j|v_k\}_{p_{v}(k)}\cdots \delta_{u_{\tilde{i}},v_{\tilde{k}};p_{u}(\tilde{i})=p_{v}(\tilde{k})}\cdots \\
&=\underbrace{\frac{N!}{\prod_{u}(n_{u}!)}}_{\sum_{p_{u}},\sum_{p_{v}=p_{u}}}\underbrace{\left(\sqrt{\frac{\prod_{u} (n_{u}!)}{N!}}\right)^2}_{\text{來自 }\langle \phi_N|,|\phi'_N\rangle\text{ 的正規化}}\sum_{j=1}^N \{u_i|\widehat{O}_j^{(I)}|u_i\}_{p_u(i)=j} \\
&=\sum_{\alpha} \{\alpha|\widehat{O}^{(I)}|\alpha\} n_{\alpha}
$$

注意這裡 $p_{\beta}$ 的選法是使得量子數集合 $\{v_i\}$ 與 $\{u_i\}$ 完全一致。在最後一個等號中，我們也已從單粒子表象切換到了佔據數表象。

* 當 $\{u_i\}=\{v_i\}$，除了 $i=i^*$ 之外都相同。這時要更小心一些，我們用 $\alpha,\beta$ 標記不同的量子數，即 $u_{i^*}=\alpha,v_{i^*}=\beta$。切換到佔據數表象後，應有

$$
\{u_i\}&\to \{\cdots,n_{\alpha},\cdots,n_{\beta},\cdots\}\\
\{v_i\}&\to \{\cdots,n_{\alpha}-1,\cdots,n_{\beta}+1,\cdots\}
$$

這裡我們以 $\{u_i\}$ 的佔據數作為參考。

$$
&\sum_{p_{u}}\sum_{p_{v}}\sum_{j=1}^N\cdots _{p_{u}(i)}\{u_i|\widehat{O}^{(I)}_j|v_k\}_{p_{v}(k)}\cdots \delta_{u_{\tilde{i}},v_{\tilde{k}};p_{u}(\tilde{i})=p_{v}(\tilde{k})}\cdots \\
&=\underbrace{\frac{N!\overbrace{n_{\alpha}}^{\beta \text{ 可接到任意一個 }\alpha}}{\prod_{u}(n_{u}!)}}_{\sum_{p_{u}}\sum_{p_{v}}}\times \underbrace{\left(\sqrt{\frac{\prod_{u} (n_{u}!)}{N!}}\right)}_{\text{來自 }\langle \phi_N|\text{ 的正規化}}\underbrace{\left(\sqrt{\frac{\prod_{v\neq\alpha,\beta} (n_{v}!)}{N!}}\sqrt{(n_{\alpha}-1)!(n_{\beta}+1)!}\right)}_{\text{來自 }|\phi'_N\rangle\text{ 的正規化}}\times\\
&\sum_{j=1}^N \{u_{i^*}|\widehat{O}_j^{(I)}|v_{i^*}\}_{p_u(i^*)=p_v(i^*)} \\
&=\sqrt{n_{\alpha}(n_{\beta}+1)} \{\alpha|\widehat{O}^{(I)}|\beta\}
$$

在最後一個等號中，我們用了這個事實：對每個排列來說，只有在 $j=p_u(i^*)=p_v(i^*)$ 時，矩陣元素才會非零。

回想一下，$\widehat{O}^{(I)}$ 是厄米的，因此也必須存在對應的厄米共軛矩陣元素，而且結構類似。我們可以直接對算符做厄米共軛；這對應到 $u\leftrightarrow v$，也就是 $\alpha\leftrightarrow \beta$。因此對應的矩陣元素是

$$
\sqrt{n_{\beta}(n_{\alpha}+1)} \{\beta|\widehat{O}^{(I)}|\alpha\}\text{.}
$$

* 現在我們也就能理解，其他剩下的項為什麼都會是零。當 $u_{i^*}=\alpha_1\neq v_{i^*}=\beta_1$ 且 $u_{j^*}=\alpha_2\neq v_{j^*}=\beta_2$ 時，會出現像

$$
\cdots \{u_{i^*}|\widehat{O}_j^{(I)}|v_{i^*}\}_{p_u(i^*)=p_v(i^*)}\cdots\{u_{j^*}|v_{j^*}\}_{p_u(j^*)=p_v(j^*)}\cdots=0\text{.}
$$

總結來說，

$$
\langle \phi_N|\widehat{O}^{(I)}_{total}|\phi'_N\rangle=
\left\{
\begin{array}{c}
\sum_{\alpha}(\widehat{O})_{\alpha,\alpha}n_{\alpha}\\
\sum_{\alpha\neq \beta}(\widehat{O})_{\alpha,\beta}\sqrt{n_{\alpha}(n_{\beta}+1)}
\end{array}
\right.
$$

我們經歷了這段長推導之後，理解到雖然排列會帶來許多組合，但其中大多數項其實都為零。接下來的問題是：有沒有一種更簡潔的方法，可以系統地表示多粒子態與多粒子算符，讓我們更有效率地做這種記帳工作？這就是下一節要展示的內容。我們將引入產生與湮滅算符，並很快看到它們為什麼是表示多粒子算符的便利工具。使用產生／湮滅算符來表示多粒子算符的方式，就是**第二量子化**。

#### 玻色子的產生／湮滅算符

玻色子的產生／湮滅算符 $b^{\dagger}_k/b_k$ 定義為

$$
\begin{array}{c}
&[b_k,b_{k'}^{\dagger}]=\delta_{k,k'}\\
&[b_k,b_{k'}]=[b_k^{\dagger},b_{k'}^{\dagger}]=0
\end{array}
\text{.}
$$

這裡 $k,k'$ 是單粒子量子數，$[A,B]=AB-BA$ 是對易子。
我們所能構造出的最簡單厄米量是

$$
\widehat{n}_k=b_k^{\dagger}b_k\text{.}
$$

此刻我們還不知道 $\widehat{n}_k$ 具體代表什麼，但我們知道它是厄米的，因此可對角化。於是可以把 $\widehat{n}_k$ 的本徵態記作 $|n_k\rangle$，滿足

$$
\widehat{n}_k|n_k\rangle=n_k|n_k\rangle\text{.}
$$

其本徵值必須滿足 $n_k\ge0$，因為

$$
n_k=\langle n_k|\widehat{n}_k|n_k\rangle=\sum_m\langle n_k|b_k^{\dagger}|m\rangle\langle m|b_k|n_k\rangle=\sum_m |\langle m|b_k|n_k\rangle|^2\ge0\text{.}
$$

接著，我們可以問：當 $b_k$ 作用在 $|n_k\rangle$ 上時，效果是什麼？我們注意到

$$
[\widehat{n}_k,b_k]=-b_k
$$

把這個關係作用到 $|n_k\rangle$ 上，可得

$$
\widehat{n}_k(b_k|n_k\rangle)=(n_k-1)(b_k|n_k\rangle)
$$

所以，$b_k$ 會把量子數降低 1。
根據這個觀察，$n_k$ 的可能取值被固定為非負整數。否則，我們總能得到某個 $n_k<0$，這會違反前面的證明。如果 $n_k$ 是整數，那麼下降過程會在 $n_k=0$ 停止。

知道這點後，我們就能顯式構造 $b_k$ 在 $|n_k\rangle$ 上的作用。

假設 $b_k|n_k\rangle=c_1|n_k-1\rangle$

$$
n_k=\langle n_k|b_k^{\dagger}b_k|n_k\rangle=\langle n_k|c_1^*c_1|n_k-1\rangle=|c_1|^2
$$

因此可知 $c_1=\sqrt{n_k}e^{i\phi_1}$。這個相位可以藉由規範選擇移除，所以我們得到

$$
b_k|n_k\rangle=\sqrt{n_k}|n_k-1\rangle\text{.}
$$

利用對易關係，也能證明

$$
b_k^{\dagger}|n_k\rangle=\sqrt{n_k+1}|n_k+1\rangle\text{.}
$$

利用玻色子的產生／湮滅算符，我們可以很容易地在佔據數基底中表示 $\widehat{O}^{(I)}_{total}$：

$$
\widehat{O}^{(I)}_{total}=\sum_{\alpha,\beta} b_{\alpha}^{\dagger} [\widehat{O}^{(I)}]_{\alpha,\beta} b_{\beta}\text{.}
$$

而前面提到的矩陣元素，就可以寫為

$$
[\widehat{O}^{(I)}_{total}]_{\{n_u\},\{n_v\}}=\langle \{n_u\}|\sum_{\alpha,\beta} b_{\alpha}^{\dagger} [\widehat{O}^{(I)}]_{\alpha,\beta} b_{\beta}|\{n_v\}\rangle \text{.}
$$

#### 第二量子化表象中的玻色子哈密頓量

這裡我們建立的是一粒子算符的表示法。玻色子二粒子算符的構造可以在 {cite:p}`fetter2012quantum` 中找到，這裡留作練習。

### 還剩下什麼……

1. 費米子的第二量子化：要構造費米子的第二量子化表示，必須仔細處理相位因子。因此，我們需要引入費米子的產生／湮滅算符。

	$$
	[f_k,f^{\dagger}_{k'}]_+&=\delta_{k,k'}\\
	[f_k,f_{k'}]+&=[f^{\dagger}_k,f^{\dagger}_{k'}]_+=0
	$$
2. 這個問題的一種簡潔處理方式可參考 {cite:p}`feynman2018statistical`。
3. 利用第二量子化建立擾動理論：這基本上會牽涉到費曼圖，超出本課程範圍。
4. 其他量子力學技巧也可以改寫成第二量子化語言，例如變分法、平均場理論等。
5. 一般而言，第二量子化後的哈密頓量寫作

$$
\widehat{H}=\sum_{i,j}a_i^{\dagger}\{i|\widehat{T}|j\}a_j+\frac{1}{2}\sum_{i,j,k,l}a_i^{\dagger}a_j^{\dagger}\{ij|\widehat{V}|kl\}a_la_k \text{.}
$$

這裡的 $a_k$ 可以是玻色子或費米子算符。$\widehat{T}$ 是一粒子算符，例如動能；$\widehat{V}$ 是二粒子算符，例如庫侖交互作用。
