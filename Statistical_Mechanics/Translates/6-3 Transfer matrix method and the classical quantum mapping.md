# 轉移矩陣方法與古典-量子對映

## 轉移矩陣方法

現在我們要解具有外場的一維 Ising 模型。這裡我們會**改變記號的定義**，讓討論更精簡。

我們把具有週期性邊界條件、且有 $N(\Omega)=N$ 個自旋的一維 Ising 模型古典哈密頓量定義為

$$
-\beta H_{\Omega}(\{S_i\})=\underbrace{\beta H}_{\beta}\sum_{i=1}^{N(\Omega)}S_i+\underbrace{\beta J}_{K}\sum_{i=1}^{N(\Omega)}S_iS_{i+1}; J>0\text{.}
$$

這裡 $S_{N(\Omega)+1}=S_1$。

配分函數為

$$
Z(h,K,N(\Omega))=Tr\left[e^{h\sum_iS_i+K\sum_iS_iS_{i+1}}\right]\text{.}
$$

先從簡單的 $h=0$ 極限開始。
當 $h=0$ 時，我們可以定義鍵變數 $\eta_{i,i+1}\equiv S_iS_{i+1}$。根據定義，$\eta_{i,i+1}=\pm1$。由於鍵變數彼此之間不耦合，因此把哈密頓量寫成鍵變數後，它其實就是另一個只有磁場 $K$ 的 Ising 模型。因此，配分函數可直接寫成 $Z(h=0,K,N(\Omega))=2(2 \cosh K)^{N(\Omega)-1}$。

不過，這個方法無法推廣到有磁場 $h$ 的情況。因此，我們引入轉移矩陣方法來克服這個困難。

先看單一條鍵 $(i,i+1)$，並列出這條鍵上所有可能組態。由於每條鍵連接兩個自旋，我們可以用矩陣表示這些組態，其中列指標對應自旋 $i$，欄指標對應自旋 $i+1$。具體地，我們可以把自旋組態與對應的 Boltzmann 因子寫成

$$
\left(
\begin{array}{cc}
\uparrow_{i} \uparrow_{i+1} &\uparrow_{i} \downarrow_{i+1}\\
\downarrow_{i} \uparrow_{i+1} & \downarrow_{i} \downarrow_{i+1}
\end{array}
\right)
\xrightarrow{\text{Boltzmann 因子}}
\left(
\begin{array}{cc}
e^{K+2h} &e^{-K}\\
e^{-K} & e^{K-2h}
\end{array}
\right)\equiv \widetilde{T}^{(i,i+1)}
$$

注意 $(i,i+1)$ 只是這條鍵的標記，並不是矩陣的列／欄索引。

在非交互作用情況中，我們很熟悉整個系統的 Boltzmann 因子可分解為各個模態 Boltzmann 因子的乘積，因為指數可以相加得到總能量。那麼，在一維最近鄰耦合系統中，能不能做類似的事？我們來看兩條相鄰的鍵 $(i-1,i)$ 與 $(i,i+1)$，把它們做矩陣乘法，看看會得到什麼。

先看組態結構。這裡我們用 $\boxtimes$ 表示「把兩個組態接起來形成更大組態」，用 $\boxplus$ 表示「把組態收集在一起」。

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

可以看出，透過這種形式操作，我們產生了三自旋系統的所有 $2^3$ 種組態。（事實上，$\boxplus$ 記號只是幫助理解矩陣乘法的結構；更精確地說，這裡真正的物件應該是 rank-3 張量 $T_{S_{i-1},S_i,S_{i+1}}$。）那麼 Boltzmann 因子呢？

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

這個表示法看起來很有希望。雖然還沒完全成功，但所有自旋組態都已經被包含進來了。然而，矩陣乘積 $\widetilde{T}_{i-1,i}\widetilde{T}_{i,i+1}$ 並沒有給出對應三自旋組態的正確 Boltzmann 因子。
例如，組態 $\uparrow_{i-1}\uparrow_{i}\uparrow_{i+1}$ 的正確 Boltzmann 因子應該是 $e^{2K+3h}$，而不是 $e^{2K+4h}$。仔細想一下就會發現，誤差來自於格點 $i$ 上磁場能量被重複計數了。

這樣一來，我們立刻知道怎麼修正。考慮週期性邊界條件系統，把矩陣 $\widetilde{T}_{i,i+1}$ 改寫成

$$
\widetilde{T}^{(i,i+1)}\to T^{(i,i+1)}=T\equiv
\left(
\begin{array}{cc}
e^{K+h} &e^{-K}\\
e^{-K} & e^{K-h}
\end{array}
\right)=(e^K\cosh h)\textbf{1}+(e^{-K})\sigma_1+(e^{K}\sinh h)\sigma_3\text{.}
$$

矩陣 $T$ 就是一維 Ising 模型的轉移矩陣。用 Pauli 矩陣 $\sigma_i$ 的表示，稍後在對映到量子哈密頓量時會有用。我們可以利用它把配分函數寫成

$$
Z(h,K,N(\Omega))=\sum_{S_1=\uparrow,\downarrow}\sum_{S_2=\uparrow,\downarrow}\cdots\sum_{S_{N(\Omega)}=\uparrow,\downarrow} [T^{(1,2)}]_{S_1,S_2}[T^{(2,3)}]_{S_2,S_3}\cdots[T^{N(\Omega),1}]_{S_{N(\Omega),S_1}}=Tr[T^{N(\Omega)}]\text{.}
$$

這個表示非常有用，因為只要把 $T$ 對角化，計算就會大幅簡化。那就來對角化 $T$：

$$
T\xrightarrow{對角化}
D=
\left(
\begin{array}{cc}
\lambda_+ &0\\
0 &\lambda_-
\end{array}
\right)\text{.}
$$

其中

$$
\lambda_{\pm}=e^K\left[\cosh h\pm\sqrt{\sinh ^2 h+e^{-4K}}\right]\text{.}
$$

假設 $\lambda_+>\lambda_-$。

那麼配分函數可精確寫成

$$
Z(h,K,N(\Omega))=\lambda_+^{N(\Omega)}+\lambda_-^{N(\Omega)}=\lambda_+^{N(\Omega)}\left[1+\left(\frac{\lambda_-}{\lambda_+}\right)^{N(\Omega)}\right]\text{.}
$$

當 $N(\Omega)\to\infty$ 時，

$$
\lim_{N(\Omega)\to\infty} Z(h,K,N(\Omega))\sim \lambda_+^{N(\Omega)}.
$$

自由能密度為

$$
f(h,K)=\lim_{N(\Omega)\to\infty}\frac{F(h,K,N(\Omega))}{N(\Omega)}=-k_BT\ln \lambda_+\\
=-J-k_BT\ln\left[\cosh h\pm\sqrt{\sinh ^2 h+e^{-4K}}\right]\text{.}
$$

當 $T>0$ 時，根號中的量始終為正，因此自由能密度沒有非解析行為。這和我們先前的論證一致：一維 Ising 模型在有限溫度下沒有相變。
當 $T=0$ 時，可以看出 $e^{-4K}$ 項消失，得到

$$
f(h,K)=-J-k_BT\ln[\cosh h\pm \vert \sinh h\vert]=-J-\vert H\vert \text{.}
$$

正如先前猜測的，$f(h,K)$ 對 $H$ 是連續的，但在 $T=0$ 時對 $H$ 並不光滑。因此，磁化密度在正或負的 $H$ 下分別為 $\pm1$。我們也可以看到，一旦出現 $e^{-4K}$ 這項，這個行為就會被平滑化。

## 古典-量子對映

當我們盯著這個轉移矩陣看時，似乎可以把它和雙能階系統的量子力學做一種形式上的連結。在這種形式詮釋下，我們把對應的希爾伯特空間定義為 $|\sigma\rangle=span(|\uparrow\rangle,|\downarrow\rangle)$。矩陣的乘積就形式上像是時間演化，且 $\mathcal{i} \Delta t=a$。也就是

$$
|\sigma_{i+1}\rangle=T|\sigma_i\rangle=e^{-a\widehat{H}}\text{.}
$$

有趣的是：這裡的 $\widehat{H}$ 到底對應什麼？如果這個形式對映成立，那麼我們就把一個古典統計力學問題對映成一個量子力學系統。對古典組態的求和會對應到對路徑的求和，而這個時間演化則會成為虛時間中的演化。要找出對應的哈密頓量算符，就必須找到常數 $C,c_1,c_2,c_3$，使得

$$
T=C\exp[c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]=\exp[log(C)+c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]\text{.}
$$

利用

$$
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n}&=r^{2n}\\
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n+1}&=r^{2n}(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)\\
r&=\sqrt{c_1^2+c_2^2+c_3^2}\text{,}
$$

可以求得

$$
C&=\sqrt{2\sinh 2K}\\
c_2&=0\\
c_3&=c_1 e^{2K}\sinh h
$$

而 $c_1$ 則滿足

$$
\tanh\left[c_1\sqrt{1+e^{4K}\sinh^2 h}\right]=\frac{\sqrt{1+e^{4K}\sinh^2 h}}{e^{2K}\cosh h}\text{.}
$$

當 $h=0$ 時，表達式簡化成

$$
C&=\sqrt{2\sinh 2K}\\
c_1&=\tanh^{-1}e^{-2K}\\
c_2&=0\\
c_3&=0\text{.}
$$

因此

$$
\widehat{H}=-\frac{1}{a}\left[\frac{1}{2}\log(2\sinh 2K)+c_1\sigma_1\right]\text{.}
$$

通常我們會忽略那個常數能量平移，只保留第二項。
極限 $a\to0$ 稱為**哈密頓量極限**。若 $a\to0$，而我們希望 $\widehat{H}$ 是一個良好定義、可詮釋為哈密頓量算符的量，那就需要 $c_1\sim a\to0$。當 $c_1\to0$ 時，$\tanh c_1\sim c_1=e^{-2K}\sim a$，這表示在取 $a\to0$ 時，$ae^{2K}$ 應該保持固定。也就是說，若要得到合理的哈密頓量算符，我們必須同時取 $a\to0$ 與 $K\to\infty$，並要求 $ae^{2K}$ 維持常數。

為了在 $a\to0$ 的同時，讓這個哈密頓量算符仍保留原本的物理性質（例如關聯長度），我們就必須相應地調整 $K\to\infty$。這其實就是最簡單的重整化群方程。（為什麼？）
