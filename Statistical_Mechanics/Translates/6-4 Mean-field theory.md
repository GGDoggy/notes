# 平均場理論

## 為什麼要用平均場理論？

不幸的是，轉移矩陣方法無法推廣到一維以上的系統。因此，我們需要其他方法來研究交互作用系統。這裡要介紹的是一種通用而簡單的方法，也就是平均場理論。平均場理論大概是研究交互作用問題時最簡單的自洽方法之一；它也很適合用來表達人們對物理圖像的「猜想」。不過，也正因為它非常一般且形式簡單，這個方法給出的結果未必穩健，甚至可能在**質性上**就是錯的。接下來，我們會先用一個具體例子介紹平均場理論的精神，包括較直接的方法與較形式化的變分方法。之後，我們會討論它背後的結構，並理解它為什麼可能給出質性錯誤的答案。最後，我們會簡單說明平均場理論與 Landau 理論的關係。

我們聚焦在 $D$ 維超立方晶格上的 Ising 模型。其配位數 $z=2D$，因為在每一個正交方向上，我們都可以向前或向後移動一格。

## Weiss 平均場理論

從前面對 Ising 模型的研究中，我們知道如何求解 $J=0$ 的模型，也就是自旋彼此不交互作用，只受外加磁場 $H$ 影響的雙能階系統，其哈密頓量為 $H_0=-H\sum_{i}S_i$。對應的磁化密度為 $M=\tanh\left(\beta H\right)$。

現在我們面對的問題是：要如何求解有交互作用的情況
$H_{\Omega}=-J\sum_{\langle i,j\rangle} S_iS_j-H\sum_i S_i$，其中 $J>0$？如果我們盯著最麻煩的那一項看，或許會發現它其實和磁場項有點類似，也就是

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{(JS_i)}_{H_i ?}S_j\text{.}
$$

如果採用這個類比，就會遇到一個問題：這個誘發出來的磁場 $H_i$ 依賴格點 $i$ 上自旋本身的行為。系統的最終解應該由精確機率分佈函數 $P_E(\{S_i\})$ 描述。雖然我們還不知道答案，但直觀上，這個分佈函數應該描述每個格點上 $S_i$ 的統計行為。原則上分佈函數可能很複雜，但我們的物理圖像暗示它應該傾向讓所有自旋彼此對齊，因此每個格點上的 $S_i$ 應該有非零期望值，也就是在低溫極限下我們預期 $\langle S_i\rangle_E=M_i\neq0$。目前我們還不知道這個期望值是否會依賴位置 $i$，所以先保留索引。

這個想法看起來很有希望。那要怎麼把它寫成方程式？我們可以把哈密頓量寫成

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{J\left[\left( S_i-\langle S_i\rangle_t \right)+\langle S_i\rangle_t \right]}_{H_i ?}S_j\text{.}
$$

此時，我們還不知道期望值是什麼；這個式子目前只是把東西重寫而已。用來計算期望值的試探分佈函數 $P_t(\{S_i\})$ 也還沒決定。（這裡 $\langle\rangle_t$ 表示用試探分佈函數算出的期望值。）

Weiss 平均場理論做出的假設是：$\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$，也就是漲落可以忽略。接著，我們利用這個假設去找看看，能不能找到一個自洽的解 $P_t(\{S_i\})$，使得確實滿足 $\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$。為了簡化記號，我們定義 $\langle S_i\rangle_t=m_i$。（如果運氣很好，找到的自洽解剛好就是精確解，也就是 $P_t(\{S_i\})=P_E(\{S_i\})$，那麼自然有 $\langle (S_i-\langle S_i\rangle_t)\rangle_E=0$。）這個大膽假設導致我們得到平均場哈密頓量

$$
H_{MFT}=-\sum_{\langle i,j\rangle} (H+J\langle S_i\rangle_t)S_j\xrightarrow{m_i=m}-\underbrace{(H+zJ m)}_{H_{eff}}\sum_jS_j\text{.}
$$

在最後一個式子裡，我們又進一步假設 $m_i$ 與格點無關，可以統一寫成 $m$。如果再盯著最後這個式子看，就會發現：它其實又變回了一個只是在「外加」磁場下的非交互作用自旋系統。

此時，我們其實已經對試探分佈函數隱含施加了一個條件：它必須產生我們想要的磁化值 $m$。另一方面，由於這個系統看起來像是處在有效磁場 $(H+zJm)$ 下的非交互作用自旋系統，因此我們也知道該系統對應的分佈函數會由有效磁場 $(H+zJm)$ 所參數化。於是，自洽條件就出現了！我們實際上是在問：對哪一個 $m$ 而言，由 $H+zJm$ 所參數化的試探分佈函數 $P_t(\{S_i\})$，其單自旋期望值恰好也是 $m$？而我們知道在這個系統中，單一自旋的期望值就是 $\tanh\left[\beta(H+zJm)\right]$。所以自洽方程為

$$
m=\tanh\left[\beta(H+zJm)\right]\text{.}
$$

這個方程的質性行為只是個簡單計算問題，因此留作練習。

從邏輯上看，我們在這裡做了幾個假設：

1. 「漲落」很小：$\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$
2. 平均場參數 $m_i$ 在空間上是均勻的。
3. 我們能夠自洽地解這個方程。

*在這個簡單問題裡，也可以看出平均場理論其實隱含地假設了分佈函數可以因式分解，也就是 $P_t(\{S_i\})=\prod_iP_{t,i}(S_i)$。*

滿足自洽方程是平均場理論成立的必要條件，但不是充分條件。問題在於：即便我們找到一個滿足自洽方程的試探分佈函數，也不代表漲落真的很小。更重要的邏輯問題是：即便能夠推導出自洽的試探分佈函數，也不保證它在質性上真正抓住了精確分佈函數的物理圖像。

因此，平均場理論是一種方便而直接的方式，用來把物理圖像形式化；但它的侷限也正來自上述這些原因。

## 變分平均場理論

Weiss 平均場理論的物理圖像很清楚；但平均場理論背後的一般結構，未必同樣清楚。因此，這裡我會再介紹另一種建立平均場理論的方法，也就是變分平均場理論。

這個方法依賴下面這個不等式：

$$
\langle e^{f(x)}\rangle\ge e^{\langle f(x)\rangle}\text{.}
$$(exp_convex)

證明並不困難，所以留作練習。

現在，從配分函數開始：

$$
Z=\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]+H_0(\{S_i\})\right\}}\text{.}
$$

這裡 $H_{\Omega}$ 是我們真正想求解的交互作用哈密頓量，$H_0$ 則是我們已知其行為的非交互作用試探哈密頓量。這個式子目前同樣只是重寫。接著可以改寫為

$$
Z=Z_0\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]\right\}} \left[\frac{e^{-\beta H_0(\{S_i\})}}{Z_0}\right]=\langle e^{-\beta(H_{\Omega}-H_0)}\rangle_0
$$

其中

$$
Z_0=\sum_{\{S_i\}}e^{-\beta H_0(\{S_i\})}=e^{-\beta F_0}=e^{-\beta(\langle H_0\rangle_0-TS_0)}\text{.}
$$

這裡 $\langle \rangle_0$ 表示對由試探哈密頓量 $H_0$ 所生成之正則系綜機率分佈取平均。利用 [inequlity](exp_convex)，我們有

$$
Z\ge Z_0 e^{-\beta\langle H_{\Omega}-H_0\rangle_0}\equiv Z_{MFT}
$$

這個方法的想法是：我們要找出某個 $H_0$，讓 $Z_{MFT}$ 最大。等價地，也就是讓 $F_{MFT}\equiv -k_BT \ln Z_{MFT}$ 最小。

根據定義，可以得到

$$
f_{MFT}=N(\Omega)^{-1}F_{MFT}=N(\Omega)^{-1}(\langle H_{\Omega}\rangle_0-TS_0)\text{.}
$$

注意，交互作用哈密頓量 $H_{\Omega}$ 的期望值，是用由非交互作用試探哈密頓量 $H_0$ 所產生的分佈函數來計算的。一旦我們把平均場自由能寫成試探哈密頓量 $H_0$ 的變分參數的函數，就可以對這個變分參數做極小化，並導出自洽方程。

```{admonition} What?
:class: tip
我們這裡採用的方法，是以「序參量」 $m$ 作為變分變數。不過還有一種更一般的方法，是把試探哈密頓量對應的機率分佈本身當作變分函數，直接尋找變分極值。第二種方法更一般，但由於時間有限，這裡不展開。有興趣的讀者可以參考 {cite:p}`chaikin1995principles`。
```

現在就用簡單的 Ising 模型來看這個方法如何運作。

我們選擇一個帶有變分參數 $\lambda$ 的試探哈密頓量：

$$
H_0(\lambda)=-\lambda\sum_iS_i\text{.}
$$

根據我們對這個系統的了解，磁化 $m$ 與變分參數 $\lambda$ 之間具有一一對應關係。因此稍後我們會直接對 $m$ 做變分。

根據定義

$$
\langle S_i\rangle_0\equiv m=\frac{N_{\uparrow}-N_{\downarrow}}{N(\Omega)}\text{.}
$$

而且我們知道，$H_0$ 對應的機率分佈函數是可因式分解的。

利用這些資訊，就能很容易把 $\langle H_{\Omega}\rangle_0$ 寫出來：

$$
\langle H_{\Omega}\rangle_0=-J\sum_{\langle i,j\rangle_0 } \langle S_iS_j\rangle_0-H\sum_i\langle S_i\rangle_0=-J\sum_{\langle i,j\rangle} \langle S_i\rangle_0\langle S_j\rangle_0-H\sum_i\langle S_i\rangle_0\\
=N(\Omega)\left[-Jm^2\frac{z}{2}-Hm\right]
$$

當 $\langle S_i\rangle_0=m$ 時，熵為

$$
S_0=k_B\ln C^N_{N_{\uparrow}}\xrightarrow{\text{Stirling 近似}}=N(\Omega)k_B\left\{\ln 2-\frac{1}{2}\left[(1+m)\ln(1+m)+(1-m)\ln(1-m)\right]\right\}\text{.}
$$

利用上面這些式子，就可以建構自由能密度 $f(T,m)$。接著只要對 $m$ 取極小，也就是要求 $\frac{df}{dm}=0$：

$$
\frac{df}{dm}=-Jzm-H +k_BT\underbrace{\left[\frac{1}{2}\ln\left(\frac{1+m}{1-m}\right)\right]}_{\tanh^{-1} m}=0\text{.}
$$

因此我們得到自洽方程

$$
m=\tanh\left[\beta(Jzm+H)\right]\text{.}
$$
