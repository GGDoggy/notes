# 轉移矩陣方法與古典-量子對應

## 轉移矩陣方法

現在我們要解帶有外場的一維 Ising 模型。這裡我們會**改變記號的定義**，讓討論更精簡。

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
當 $h=0$ 時，我們可以定義鍵變數 $\eta_{i,i+1}\equiv S_iS_{i+1}$。依定義，$\eta_{i,i+1}=\pm1$。由於鍵變數彼此不耦合，將哈密頓量寫成鍵變數後，就變成另一個只有磁場 $K$ 的 Ising 模型。因此，配分函數可以直接寫成 $Z(h=0,K,N(\Omega))=2(2 \cosh K)^{N(\Omega)-1}$。

不過，這個方法無法推廣到有磁場 $h$ 的情況。這裡我們引入轉移矩陣方法來克服這個困難。

先看一條單獨的鍵 $(i,i+1)$，並考慮這條鍵上所有可能的組態。由於每條鍵上有兩個耦合的自旋，我們可以用矩陣表示這些組態。列指標對應自旋 $i$，欄指標對應自旋 $i+1$。具體來說，自旋組態與其對應的 Boltzmann 因子為

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

注意，$(i,i+1)$ 只是這條鍵的標記，並不是矩陣的列或欄索引。

在非交互作用情況下，我們很熟悉這樣的結構：整個系統的 Boltzmann 因子就是各個模態 Boltzmann 因子的乘積，因為指數加總起來就是總能量。那麼對這個一維最近鄰耦合系統，我們能不能做一樣的事？讓我們取兩條相鄰的鍵 $(i-1,i)$ 與 $(i,i+1)$，把它們做矩陣乘法，看看結果會是什麼。

先看組態本身。這裡我們用 $\boxtimes$ 表示把兩個組態接起來形成一個更大的組態，用 $\boxplus$ 表示把不同組態收集在一起。

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

可以看出，我們透過這種形式操作產生了三自旋系統的全部 $2^3$ 種組態。（事實上，這裡的 $\boxplus$ 記號只是幫助理解矩陣乘法的結構。真正的意思其實更接近 rank-3 張量 $T_{S_{i-1},S_i,S_{i+1}}$。）那麼 Boltzmann 因子呢？

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

這種表示看起來非常有希望。雖然還沒有完全成功，但所有自旋組態都已經被包含進來了。不過，矩陣乘積 $\widetilde{T}_{i-1,i}\widetilde{T}_{i,i+1}$ 並沒有給出對應組態的正確 Boltzmann 因子。
例如，組態 $\uparrow_{i-1}\uparrow_{i}\uparrow_{i+1}$ 的 Boltzmann 因子應該是 $e^{2K+3h}$，而不是 $e^{2K+4h}$。若仔細看整個過程，就會發現誤差來自格點 $i$ 上磁場能量的重複計數。

既然如此，我們很快就知道該怎麼修正。考慮具有週期性邊界條件的系統，把矩陣 $\widetilde{T}_{i,i+1}$ 改寫成

$$
\widetilde{T}^{(i,i+1)}\to T^{(i,i+1)}=T\equiv
\left(
\begin{array}{cc}
e^{K+h} &e^{-K}\\
e^{-K} & e^{K-h}
\end{array}
\right)=(e^K\cosh h)\textbf{1}+(e^{-K})\sigma_1+(e^{K}\sinh h)\sigma_3\text{.}
$$

矩陣 $T$ 就是一維 Ising 模型的轉移矩陣。用 Pauli 矩陣 $\sigma_i$ 表示的形式，之後在對應到量子哈密頓量時會有用。利用這個矩陣，我們可以把配分函數寫成

$$
Z(h,K,N(\Omega))=\sum_{S_1=\uparrow,\downarrow}\sum_{S_2=\uparrow,\downarrow}\cdots\sum_{S_{N(\Omega)}=\uparrow,\downarrow} [T^{(1,2)}]_{S_1,S_2}[T^{(2,3)}]_{S_2,S_3}\cdots[T^{N(\Omega),1}]_{S_{N(\Omega),S_1}}=Tr[T^{N(\Omega)}]\text{.}
$$

這個式子很有用，因為只要把 $T$ 對角化，計算就會大幅簡化。那麼就來把 $T$ 對角化：

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

那麼配分函數就可精確寫成

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

當 $T>0$ 時，根號中的量始終為正，因此自由能密度沒有非解析行為。這與前面所說的一維 Ising 模型在有限溫下沒有相變是一致的。
當 $T=0$ 時，可以看出 $e^{-4K}$ 消失，因此

$$
f(h,K)=-J-k_BT\ln[\cosh h\pm \vert \sinh h\vert]=-J-\vert H\vert \text{.}
$$

正如我們之前猜測的，$f(h,K)$ 對 $H$ 是連續的，但在 $T=0$ 時對 $H$ 並不光滑。因此，磁化密度在正或負的 $H$ 下分別是 $\pm1$。我們也可以看出，一旦保留 $e^{-4K}$ 項，這個行為就會被平滑化。

## 古典-量子對應

當我們盯著轉移矩陣看時，似乎可以在形式上把它和一個雙能階系統的量子力學聯繫起來。若接受這個形式詮釋，我們便定義這個形式系統的希爾伯特空間為 $|\sigma\rangle=span(|\uparrow\rangle,|\downarrow\rangle)$。矩陣的乘積形式上就像是時間演化，而 $\mathcal{i} \Delta t=a$。也就是說，

$$
|\sigma_{i+1}\rangle=T|\sigma_i\rangle=e^{-a\widehat{H}}\text{.}
$$

如果這種形式對應真的可以建立，那麼我們就得到一個從古典統計力學問題到量子力學系統的對應。對古典組態的總和對應到對路徑的總和，而這裡的時間演化則是虛時間演化。為了找出對應的哈密頓量算符，我們需要找常數 $C,c_1,c_2,c_3$，使得

$$
T=C\exp[c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]=\exp[log(C)+c_1\sigma_1+c_2\sigma_2+c_3\sigma_3]\text{.}
$$

利用

$$
\begin{align}
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n}&=r^{2n}\\
(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)^{2n+1}&=r^{2n}(c_1\sigma_1+c_2\sigma_2+c_3\sigma_3)\\
r&=\sqrt{c_1^2+c_2^2+c_3^2}\text{,}
\end{align}
$$

可以得到

$$
\begin{align}
C&=\sqrt{2\sinh 2K}\\
c_2&=0\\
c_3&=c_1 e^{2K}\sinh h
\end{align}
$$

而 $c_1$ 則滿足

$$
\tanh\left[c_1\sqrt{1+e^{4K}\sinh^2 h}\right]=\frac{\sqrt{1+e^{4K}\sinh^2 h}}{e^{2K}\cosh h}\text{.}
$$

當 $h=0$ 時，式子會簡化成

$$
\begin{align}
C&=\sqrt{2\sinh 2K}\\
c_1&=\tanh^{-1}e^{-2K}\\
c_2&=0\\
c_3&=0\text{.}
\end{align}
$$

因此

$$
\widehat{H}=-\frac{1}{a}\left[\frac{1}{2}\log(2\sinh 2K)+c_1\sigma_1\right]\text{.}
$$

通常我們會忽略常數能量平移，只保留第二項。
極限 $a\to0$ 稱為**哈密頓量極限**。如果 $a\to0$，而我們希望 $\widehat{H}$ 是一個良好定義、可詮釋為哈密頓量算符的量，就必須要求 $c_1\sim a\to0$。當 $c_1\to0$ 時，$\tanh c_1\sim c_1=e^{-2K}\sim a$，這表示在取 $a\to0$ 時，$ae^{2K}$ 應保持固定。換句話說，若要得到一個合理的哈密頓量算符，我們必須同時取 $a\to0$ 與 $K\to\infty$，並讓 $ae^{2K}$ 保持常數。

若要讓這個哈密頓量算符在 $a\to0$ 的過程中仍保留原本的物理性質（例如關聯長度），我們就必須相應地調整 $K\to\infty$。這其實就是最簡單的重整化群方程。（為什麼？）
