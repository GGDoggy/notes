# 聲子與光子

我們將討論聲子與光子的統計力學。這裡我們會簡短說明聲子與光子的起源。討論只聚焦在物理圖像與建立統計力學描述所需的形式工具。若讀者想回顧更完整的推導細節，可參考很好的教材 {cite:p}`simon2013oxford`。

## 聲子

聲子是聲波的量子。因此，為了理解聲子，我們需要先對固體中的聲波有一個粗略圖像。為了掌握核心概念，我們將聚焦於最簡單的聲子類型：簡單晶格系統中的聲子。

### 聲子的能帶結構

對稱性通常能幫助我們簡化問題分析。晶格系統具有*離散*平移對稱性。我們該如何利用這個對稱性來簡化分析？

在具有*連續*平移對稱性的系統中，動量守恆。因此我們通常用動量來標記系統的本徵態。

對於具有*離散*平移對稱性的系統，我們同樣可以使用晶體動量向量 $\textbf{k}$ 來標記本徵態。

讓我們從簡單的一維系統開始。這個系統包含兩個長度尺度。
1. 來自離散平移對稱性，其晶格常數為 $a$。也就是 $H(x)=H(x+a)$（物理約束）。
2. 通常我們還會採用週期性邊界條件，也就是 $H(x)=H(x+L)$（為了方便所做的邊界條件選擇）。為了後續方便，我們假設有 $N$ 個格點，因此 $L=Na$。

我們也知道，具有*連續*平移對稱性的系統，其本徵態是 $e^{ipx/\hbar}=e^{ikx}$。而*離散*平移對稱性可以看作是*連續*平移對稱性的子集合，也就是我們只考慮在位移 $a$ 與 $L=Na$ 下保持不變的那些態。這自然導致兩種特徵性的晶體動量向量：
1. $e^{iGa}=1$，其中 $G=G_0 m$、$G_0=\frac{2\pi}{a}$ 且 $m\in\mathcal{Z}$。$G_0$ 在倒空間中形成倒晶格。
2. $e^{iqL}=1$，其中 $q=q_0 n$、$q_0=\frac{2\pi}{L}=\frac{1}{N}G_0$ 且 $n\in\mathcal{Z}$。$q$ 是倒空間中的波向量。通常當 $L\to\infty$ 時，我們有 $q_0\to0$。倒空間中每個 $q$ 對應的能量會形成一條能帶。依激發的性質不同，它可能是我們稍後要討論的聲子能帶，也可能是電子能帶。

具有*連續*與*離散*平移對稱性的系統之間，關鍵差別在於守恆律。對於具有*連續*平移對稱性的系統，守恆的是動量；對於具有*離散*平移對稱性的系統，守恆的是*準動量*（或*晶體動量*）。*準動量*守恆的意思是，波向量 $q$ 只在加上整數倍的 $G_0$ 之下才有唯一性，也就是 $q\equiv q+G_0$。為什麼會這樣？這與一個事實有關：對波向量分別為 $q$ 與 $q+G_0$ 的連續波來說，它們在離散取樣後的表示是無法區分的。這個現象稱為 *wave aliasing*。可參考 [wikipedia link](https://en.wikipedia.org/wiki/Crystal_momentum) 與 [wikipedia gif](https://en.wikipedia.org/wiki/Crystal_momentum#/media/File:Quasimomentum.gif)。

由於準動量守恆，我們通常只聚焦於 $q\in(-G_0/2,G_0/2]$ 這個區域。這個區域稱為第一布里淵區。

通常當我們翻開固態物理課本時，會在第一布里淵區中看到兩條聲子能帶。其中在 $\lim_{|q|\to0}E(q)\propto |q|$ 極限下無能隙的分支，稱為聲學聲子；而有能隙的分支，則稱為光學聲子。

在上一節中，我們討論了 $N$ 個彼此解耦的量子簡諧振盪子。若有能隙的模態近似與 $q$ 無關，則它們可以看作是光學聲子的良好近似。事實上，這就是愛因斯坦的聲子模型 {cite:p}`einstein1907plancksche`。

### 一維古典聲波

這裡我們要討論一個簡單例子，也就是一維耦合振盪子。這是一個可以解析處理的模型。不過，和所有簡單模型一樣，我們應該關心的是這類系統的普遍特徵，而不是過度聚焦於模型過度簡化所帶來的人為假象。稍後我會解釋這句話的意思。

我們先聚焦於古典系統。之後便可導出能量作為 $q$ 的函數。再接著，我們直接採用從古典到量子的替換捷徑：$E(q)=\hbar\omega(q)\to\hbar\omega(q)\left(\frac{1}{2}+\hat{n}_q\right)$。其中 $\hat{n}_q$ 是波向量為 $q$ 的量子振盪子的量子數。

開始分析吧。考慮 $N$ 個質量為 $m$ 的粒子，彼此透過彈性位能 $\frac{\kappa}{2}\Delta x^2$ 的彈簧耦合。這裡 $\kappa$ 是力常數，$\Delta x$ 是相對平衡位置的位移。我們假設粒子的平衡位置形成一個晶格，其晶格常數為 $a$。

系統的總位能是

$$
V_{\text{total}}(\left\{x_i\right\})=\sum_i V(x_{i+1}-x_i)\approx\sum_i\frac{\kappa}{2}\left(x_{i+1}-x_i-a\right)^2=\sum_i\frac{\kappa}{2}\left(\delta x_{i+1}-\delta x_i\right)^2\text{.}
$$

其中 $\delta x_i=x_i-x_{i,eq}$。

施加在第 $n$ 個粒子上的總力為

$$
F_n=-\frac{\partial V_{\text{total}}(\left\{x_i\right\})}{\partial x_n}=m\frac{\partial ^2 \delta x_n}{\partial t^2} = \kappa\left[\left(\delta x_{\text{n+1}}-\delta x_{n}\right)-\left(\delta x_n-\delta x_{n+1}\right)\right]\text{.}
$$

若我們用試探解 $\delta x_n=A e^{i\omega t-iqx_{n,eq}}$ 來解這些方程，就得到

$$
m\omega^2=2\kappa(1-\cos qa);\omega(q)=2\sqrt{\frac{\kappa}{m}}\vert\sin\frac{qa}{2}\vert\text{.}
$$

函數形式 $\omega(q)=2\sqrt{\frac{\kappa}{m}}\vert\sin\frac{qa}{2}\vert$ 本身並不是普遍的；真正普遍的結構是 $\lim_{q\to0}\omega(q)\approx vq$。這種線性色散模態與 Goldstone 定理有關。當一個連續對稱性自發破缺時，就會出現線性色散模態。在這裡，被自發破缺的是連續平移對稱性。對稱性破缺之後，就得到我們的聲子模型。

對於量子化系統而言，每一個模態 $q$ 都對應到一個頻率為 $\omega(q)$ 的量子簡諧振盪子。此外，聲子模態還具有極化。在三維各向同性系統中，極化數為 3。我們用 $\alpha$ 來標記每個模態的極化。

一般而言，配分函數應寫為

$$
Z=\sum_{\left\{n_{q,\alpha}\right\}} \exp\left[-\beta \sum_{q,\alpha} \hbar\omega_{\alpha}(q)\left(\frac{1}{2}+n_{q,\alpha}\right)\right]\xrightarrow{\text{factorize}}\prod_{q,\alpha}\left\{\sum_{n_{q,\alpha}}\exp\left[-\beta \hbar\omega_{\alpha}(q)\left(\frac{1}{2}+n_{q,\alpha}\right)\right]\right\}\text{.}
$$

為了聚焦於重點，後面的討論中我們假設色散關係是各向同性的，並把離散求和改寫為積分。

### Debye 模型

如前所述，$\omega(q)$ 依賴於系統細節。由 Goldstone 定理帶來的普遍特徵是，在 $q\to0$ 時有 $\omega(q)\sim vq$。另一個限制則是，這個量子模型在古典極限下，其比熱應回到三維系統的 $3Nk_B$。為了把這兩個普遍特徵合併進同一個模型中，Debye 提議把整個頻譜線性化，並手動加上一個頻率截止。下面看看這是怎麼做的。

1. 線性色散模態：假設 $\omega(q)=vq$ 且 $dq=v^{-1}d\omega$。那麼能量期望值可寫成

	$$
	\langle \hat{H}\rangle=E\approx 3(4\pi)\left(\frac{L}{2\pi v}\right)^3\int_0^\infty \omega^2 d\omega \exp\left[-\beta \hbar\omega(q)\left(\frac{1}{2}+\langle \hat{n}_q\rangle\right)\right]\\
=\int_0^{\infty}d\omega g(\omega)\hbar\omega(\frac{1}{2}+n_B(\beta\hbar\omega))
	$$

	其中 $g(\omega)$ 是態密度，表示在能量窗 $[\omega,\omega+d\omega]$ 內的態數，已包含極化自由度。$n_B(\beta\hbar\omega)=\frac{1}{e^{\beta\hbar\omega}-1}$。
	經過一些代數整理後，我們得到
	
	$$
	g(\omega)=N\frac{9\omega^2}{\omega_d^3};\omega_d^3=6\pi^2\frac{N}{L^3}v^3\text{.}
	$$

	把積分變數改成無因次參數 $x=\beta\hbar\omega$ 之後，就有
	
	$$
	\langle \hat{H}\rangle=\frac{9N\hbar}{\omega_d^3} (\beta \hbar)^{-4}\underbrace{\int_0^{\infty} dx\frac{x^3}{e^x-1}}_{\pi^4/15}+\text{與溫度無關的常數。}
	$$

	因此我們可得玻色子線性色散模態的比熱為
	
	$$
	C=\frac{\partial E}{\partial T}\propto T^3
	$$
   
1. 頻率截止：比熱的 $T^3$ 行為與線性色散模態緊密相關。若這個行為不改變，它就會一路延伸到 $T\to\infty$ 的極限。顯然這不是我們期待的古典行為。要怎麼修正？Debye 的作法是在頻率積分上加一個截止值 $\omega_{cutoff}$，使得截止頻率以下的模態總數恰好等於這個系統的總模態數 $3N$，也就是
	
	$$
	\int_0^{\infty}d\omega\to\int_0^{\omega_{cutoff}} d\omega=3N\text{.}
	$$
	
	加入這個截止後，能量期望值變成
	
	$$
	\langle \hat{H}\rangle=\int_0^{\omega_{cutoff}}d\omega g(\omega)\hbar\omega(\frac{1}{2}+n_B(\beta\hbar\omega))\xrightarrow{\beta\hbar\omega\to0}\int_0^{\omega_{cutoff}}d\omega g(\omega)\hbar\omega(\beta\hbar\omega)^{-1}\approx 3Nk_BT\text{.}
	$$

	因此我們恢復了古典極限，亦即 $C\to 3Nk_B$。

## 光子

聲子的計算與光子的情形非常相似。這裡我只列出幾個關鍵差異，詳細推導留作練習。

1. 完全線性色散。
2. 其速度大小就是光速。
3. 由於規範性質，光子的極化數是 2。在三維空間中，光子的極化自由度數目為 2。
