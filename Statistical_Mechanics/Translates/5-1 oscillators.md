# 振盪子

到目前為止，我們處理的都是自由系統，例如理想氣體（自由粒子）與自旋的順磁相（自由的二元變數）。現在我們可以試著探討另一種情況：粒子彼此之間雖然仍可視為不互動，但會受到外部位能的影響。最重要的例子就是振盪子。

## 溫度為 $T$ 的一維古典振盪子

讓我們依照上一節的流程圖來研究這個系統。

| 階段  |                   統計力學觀念                    |                                                                                                                物理系統                                                                                                                 |
| :-: | :-----------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|  1  |                   選定一個系統                    |                                                                                                            一群彼此獨立的古典振盪子                                                                                                             |
|  2  |              找出相關的微觀自由度 $\xi$               |                                                                                                       振盪子的座標與動量 $(R_i,P_i)$。                                                                                                        |
|  3  |              為微觀自由度建立可能的能量形式。               |                                                             在這個例子中，哈密頓量已知，因此不需要煩惱如何寫下對應的哈密頓量。基本上，$H=\sum_{i=1}^N H_i$，其中 $H_i=\frac{P_i^2}{2m}+\frac{\kappa}{2}R_i^2$。                                                              |
|  4  |    根據系統的限制選擇合適的系綜。由於溫度 $T$ 固定，所以選擇正則系綜。     | 多數實驗研究的是固定溫度下的平衡系統，因此我們通常選擇正則系綜。依照先前在統計力學中的知識，我們知道如何建構配分函數。對本系統而言，$Z=\int \left(\prod_{i=1}^N\frac{dR_idP_i}{h}\right) \exp\left[-\beta \sum_{j=1}^N \frac{1}{2m}P_j^2+\frac{m\omega_0^2}{2}R_j^2\right]$，其中 $\omega_0^2=\kappa/m$。 |
|  5  | 藉由和實驗比較來修正對 $\xi$ 與 $H(\xi)$ 的猜測。（回到第 2 階段） |                                                                                                     由於這題的哈密頓量已經給定，因此不需要再拿實驗來比較。                                                                                                     |

潛在障礙 1 在這裡不存在，因為這是一個教學型問題。潛在障礙 2 則是：我們是否能把配分函數算出來。

$$
Z\xrightarrow{\text{interacting free}} \prod_{i=1}^{N}\left[\int \frac{dR_idP_i}{h} \exp\left[-\left(\frac{\beta}{2m}\right) P_i^2\right]\exp\left[-\left(\frac{\beta m\omega_0^2}{2}\right) R_i^2\right]\right]=\left(\frac{1}{\beta \hbar\omega_0}\right)^N\text{.}
$$

對這種「可分離但受外勢影響」的系統而言，最重要的結構是總能量可以寫成各個自由度能量的總和。這個性質會自動導致配分函數可以因式分解。因此，整個系統的配分函數就是各個單一自由度配分函數的乘積。這裡我把積分留作練習，因為它不過就是對動量與座標做高斯積分。

系統的能量期望值與比熱為

$$
\langle H\rangle=E=\frac{\partial \ln Z}{\partial (-\beta)} =Nk_BT; C=\frac{\partial E}{\partial T}=Nk_B\text{.}
$$

我們可以觀察到兩個非常重要的結構：
1. 結果與 $\omega_0$ 無關。
2. 動量空間與位置空間中的高斯積分，各自對比熱貢獻 $\frac{k_BT}{2}$。

### 等分配定理

假設我們系統的哈密頓量可近似寫成

$$
H=H_0(X_1,X_2,\cdots,X_r)+ H_1(X_{r+1},\cdots, X_N)\text{.}
$$

這裡的 $H_0$ 是其自變數的二次型能量部分。因此我們有

$$
\sum_{i=1}^r X_i\frac{\partial H_0}{\partial X_i}=2H_0\text{.}
$$

這裡我們只關注 $H_0$ 所帶來的效果。來自 $H_0$ 的能量期望值為

$$
\langle H_0\rangle =\frac{1}{Z}\int \left(\prod_{i=1}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \underbrace{H_0(X_1,\cdots, X_r)}_{\frac{1}{2}\sum_{l=1}^r X_l\frac{\partial H_0}{\partial X_l}} \exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\text{.}
$$

現在我們注意到

$$
X_l\frac{\partial }{\partial X_l}\left[\exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\right]\\
=X_l(-\beta \frac{\partial }{\partial X_l}H_0(X_1,\cdots,X_r))\exp\left[ -\beta (H_0(X_1,\cdots,X_r)+H_1(X_{r+1},\cdots, X_N)\right]\text{.}
$$

利用這個恆等式，我們得到

$$
\langle H_0\rangle =\frac{-k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)} \\
=\frac{-k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1,i\neq l}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \int dX_l X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)}
\text{.}
$$

這裡我們省略了 $H_0$ 與 $H_1$ 的自變數，讓記號更精簡一些。我們也先專注在對 $X_l$ 的積分。

$$
\int dX_l X_l\frac{\partial }{\partial X_l} e^{-\beta(H_0+H_1)}=\underbrace{\left. X_l e^{-\beta(H_0+H_1)}\right|_{-\infty}^{\infty}}_{=0, \because \left.e^{-\beta H_0}\right|_{\pm\infty}\to0}-\int dX_le^{-\beta(H_0+H_1)}
$$

因此，原式可化簡為

$$
\langle H_0\rangle 
=\frac{k_BT}{2}\frac{1}{Z}\sum_{l=1}^r\int \left(\prod_{i=1,i\neq l}^r dX_i\right)\left(\prod_{j=r+1}^N dX_j\right) \int dX_l e^{-\beta(H_0+H_1)}=\frac{k_BT}{2} \frac{1}{Z} (rZ)= r\frac{k_BT}{2} 
\text{.}
$$

所以我們看到，每一個二次模態對能量期望值的貢獻都是 $\frac{k_BT}{2}$。簡諧振盪子與理想氣體只是這個定理的特例。

* 理想氣體模型：能量對動量是二次的。在三維中，每個粒子貢獻 $3\times \frac{k_BT}{2}$。因此 $N$ 粒子系統的內能是 $\frac{3Nk_BT}{2}$。
* 振盪子：能量對動量與座標都是二次的。在一維中，每個振盪子貢獻 $2\times \frac{k_BT}{2}$。$N$ 個一維振盪子的內能是 $Nk_BT$。

## 量子簡諧振盪子

我們將以類似的程序分析這個系統。

| 階段  |                   統計力學觀念                    |                                                                                                                                                                                                                                                                                                                                                                                                                                            物理系統                                                                                                                                                                                                                                                                                                                                                                                                                                             |     |
| :-: | :-----------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|  1  |                   選定一個系統                    |                                                                                                                                                                                                                                                                                                                                                                                                                                        一群彼此獨立的量子振盪子                                                                                                                                                                                                                                                                                                                                                                                                                                         |     |
|  2  |              找出相關的微觀自由度 $\xi$               |                                                                                                                                                                                                                                                                                                                                                                                          每個振盪子的波函數 $\vert \phi_{n}^{(i)}\rangle$，其中 $i=1\sim N$，能量為 $E_n=\left(n+\frac{1}{2}\right)\hbar \omega$。                                                                                                                                                                                                                                                                                                                                                                                           |     |
|  3  |              為微觀自由度建立可能的能量形式。               |                                                                                                                                                                                                                                                                                                                在這個例子中，哈密頓量已知，因此不需要煩惱如何寫下對應的哈密頓量。基本上，$\hat{H}=\sum_{i=1}^N \hat{H}_i$，而 $\hat{H}_i=\frac{\hat{P}_i^2}{2m}+\frac{\kappa}{2}\hat{R}_i^2=\left(\hat{n}_i+\frac{1}{2}\right)\hbar\omega$。這裡的位置、動量與哈密頓量都被提升為量子算符。並且 $[X_i,P_i]=i\hbar$、$\omega=\frac{\kappa}{m}$。                                                                                                                                                                                                                                                                                                                 |     |
|  4  |    根據系統的限制選擇合適的系綜。由於溫度 $T$ 固定，所以選擇正則系綜。     | 多數實驗研究的是固定溫度下的平衡系統，因此我們通常選擇正則系綜。依照先前的統計力學知識，我們知道如何建構配分函數。對本系統而言，$Z=\sum_{n_1=0}^{\infty}\sum_{n_2=0}^{\infty}\cdots \sum_{n_N=0}^{\infty}\exp\left[-\beta\left(\sum_{j=1}^{N}\left(n_j+\frac{1}{2}\right)\hbar\omega\right)\right]$。由於系統可分離，配分函數可以因式分解，因此 $Z=\zeta^N$。其中 $\zeta=\sum_{n=0}^{\infty}\exp\left[-\beta\left(n+\frac{1}{2}\right)\hbar\omega\right]=\frac{e^{\frac{-\beta \hbar\omega}{2}}}{1-e^{-\beta\hbar\omega}}$。最後一個等號是因為這是一個可顯式求和的等比級數。有了配分函數後，就能依照標準程序得到能量 $E=\frac{\partial \ln Z}{\partial (-\beta)}=N\hbar\omega\left(\frac{1}{2}+n_B(\beta \hbar\omega)\right)=N\hbar\omega\left(\frac{1}{2}+\frac{1}{e^{\beta\hbar\omega}-1}\right)$，以及 $C=\frac{\partial E}{\partial T}=Nk_B\left[(\beta\hbar\omega)^2\frac{e^{\beta\hbar\omega}}{(e^{\beta\hbar\omega}-1)^2}\right]$。當 $\beta\hbar\omega\to0$ 時，比熱趨近 $Nk_B$；而在 $\beta\hbar\omega\to\infty$ 的極限下，系統的量子性會使比熱呈指數抑制。 |     |
|  5  | 藉由和實驗比較來修正對 $\xi$ 與 $H(\xi)$ 的猜測。（回到第 2 階段） |                                                                                                                                                                                                                                                                                                                                                                                                                                 由於這題的哈密頓量已經給定，因此不需要再拿實驗來比較。                                                                                                                                                                                                                                                                                                                                                                                                                                 |     |


>[!TIP] What?
量子系統的配分函數到底是什麼意思？
看起來我們似乎還是在對古典系統做計算，唯一的差別只是能量被量子化了。
> 
> 在古典系統中，我們說有一個微觀組態 $\xi$，其機率與 $e^{-\beta H(\xi)}$ 成正比。也就是說，我們有一個由許多微觀組態組成的系綜，並依此給定其機率分佈。
> 
> 在量子系統中，我們說有一個能量本徵態 $\vert E_n\rangle$，其機率與 $e^{-\beta E_n}$ 成正比。也就是說，在我們的系綜中有一組狀態，其古典機率分佈與 $e^{-\beta E_n}$ 成正比。細心的讀者可能會問：波函數的資訊去哪裡了？配分函數不是應該幫助我們計算系統的期望值嗎？而在量子力學中，觀察量的平均值不應該要算像 $\langle \psi\vert \hat{O}\vert\psi\rangle$ 這樣的量嗎？沒錯，確實如此。這裡之所以可以避免這個複雜性，是因為我們選擇的觀察量是哈密頓量，而對於系綜中的態 $\vert E_n\rangle$，其量子期望值滿足 $\langle E_n\vert \hat{H}\vert E_n\rangle=E_n$。這個資訊已經被包含在配分函數裡。如果我們想計算系統的質心，就需要取 $\hat{O}=\sum_i \hat{x}_i$，那麼我們就必須真的去算 $\langle E_n\vert \sum_i\hat{x}_i\vert E_n\rangle$；這部分的資訊並不包含在配分函數中。
> 
> 也就是說，量子系統系綜的一般定義需要兩種資訊。一種是狀態集合的古典機率，另一種是對應的波函數。在統計力學中，我們透過波茲曼因子得到古典機率。更一般地，系統必須用密度矩陣來定義。能量表象下的密度矩陣為
> 
> $$
> \hat{\rho}=\sum_{E_n} P(E_n)\vert E_n\rangle\langle E_n\vert=\sum_{E_n} \frac{\vert E_n\rangle e^{-\beta E_n}\langle E_n\vert}{Z}=\frac{e^{-\beta \hat{H}}}{Z}\sum_{E_n} \vert E_n\rangle \langle E_n\vert=\frac{e^{-\beta \hat{H}}}{Tr\left[e^{-\beta \hat{H}}\right]}\text{.}
> $$
> 
> 觀察量 $\hat{O}$ 的期望值是
> 
> $$
> \langle \hat{O}\rangle=\sum_{E_n} P(E_n)\langle E_n\vert\hat{O}\vert E_n\rangle=Tr\left[\hat{\rho} \hat{O}\right]\text{.}
> $$
> 
> 我們可以看到，期望值裡其實有兩種「平均」。一種是來自對 $P(E_n)$ 的統計平均；另一種是來自 $\langle E_n\vert\hat{O}\vert E_n\rangle$ 的量子平均。當我們選擇計算哈密頓量的期望值時，量子平均就變得非常平凡。這也是為什麼我們對能量期望值的計算看起來相當「古典」。
> 
> 另一個有趣的問題是：當我們從古典統計力學走向量子統計力學時，是否會出現質上的差異？事實證明，牛頓第二定律與薛丁格方程之間存在本質差別。牛頓方程很容易出現非線性效應；然而薛丁格方程是線性的。這意味著，在量子系統裡，混沌的概念需要被重新思考。目前，一個封閉量子系統如何達到熱平衡仍然是研究主題。讀者可參考 {cite:p}`nandkishore2014many` 以獲得更多資訊。

## 從這兩個例子應學到的重點

這兩個例子展示了幾個重要觀念：
1. 當能量是離散量子化或連續變數時，該如何建構配分函數？答案就是：求和與積分。
2. 配分函數之所以可因式分解，是因為系統彼此不互動。這個性質的根源在於：對於可分離系統，總能量可以直接寫成各部分能量的總和。
