# 平均場理論

## 為什麼要用平均場理論？

不幸的是，轉移矩陣方法無法推廣到一維以上的系統。因此，我們需要其他方法來研究交互作用系統。這裡我們要介紹一種通用且簡單的方法，也就是平均場理論。平均場理論大概是研究交互作用問題時最簡單的自洽方法之一。它也是描述人們對物理圖像「猜測」的強大工具。不過，也正因為它很一般、又很簡單，這個方法得到的結果未必穩健，甚至可能在**質性上**是錯的。我們會先用一個具體例子，透過較直接的方法與較形式化的變分方法來介紹平均場理論。之後，我們會討論它的結構，並理解它為什麼可能給出質性錯誤的答案。最後，我們會說明平均場理論與 Landau 理論之間的關係。

我們聚焦在 $D$ 維超立方晶格上的 Ising 模型。其配位數為 $z=2D$，因為在每個正交方向上，我們都可以向前或向後移動一格。

## Weiss 平均場理論

從先前對 Ising 模型的研究中，我們知道如何解 $J=0$ 的模型，也就是非交互作用的雙能階自旋系統，在外加磁場 $H$ 下由哈密頓量 $H_0=-H\sum_{i}S_i$ 描述。對應的磁化密度為 $M=\tanh\left(\beta H\right)$。

我們現在面對的問題是：如何處理交互作用情況
$H_{\Omega}=-J\sum_{\langle i,j\rangle} S_iS_j-H\sum_i S_i$，其中 $J>0$？如果盯著最麻煩的那一項看，我們可能會覺得它其實有點像磁場項的效果，也就是

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{(JS_i)}_{H_i ?}S_j\text{.}
$$

若採用這個類比，我們就會碰到一個問題：誘發出來的磁場 $H_i$ 依賴於格點 $i$ 上自旋本身的行為。系統的最終解應該由精確機率分佈函數 $P_E(\{S_i\})$ 描述。雖然我們還不知道答案，但我們預期這個分佈函數會描述各個格點上 $S_i$ 的統計行為。原則上，分佈函數可以是任何形式；但從物理圖像來看，我們預期它應該傾向讓所有自旋彼此對齊，因此在低溫極限下應該給出 $\langle S_i\rangle_E=M_i\neq0$。目前我們還不知道這個期望值是否依賴於格點 $i$，所以先保留索引。

這個想法看起來很有希望。那麼應該怎麼把它寫成方程式？我們可以把哈密頓量寫成

$$
-J\sum_{\langle i,j\rangle} S_iS_j\stackrel{?}{\to}-\sum_{\langle i,j\rangle} \underbrace{J\left[\left( S_i-\langle S_i\rangle_t \right)+\langle S_i\rangle_t \right]}_{H_i ?}S_j\text{.}
$$

目前我們還不知道期望值是什麼，因此這其實只是把式子重寫而已。用來計算期望值的試探分佈函數 $P_t(\{S_i\})$ 也尚未決定。（這裡我們用 $\langle\rangle_t$ 表示以試探分佈函數計算的期望值。）

Weiss 平均場理論做出的假設是：$\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$，也就是漲落可以忽略。接著，我們就在這個假設下，去尋找是否存在某個自洽的解 $P_t(\{S_i\})$，使得 $\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$ 確實成立。為了簡化記號，我們把 $\langle S_i\rangle_t$ 記為 $m_i$。（若我們夠幸運，使自洽解剛好就是精確解，也就是 $P_t(\{S_i\})=P_E(\{S_i\})$，那麼自然有 $\langle (S_i-\langle S_i\rangle_t)\rangle_E=0$。）這個大膽假設導致平均場哈密頓量

$$
H_{MFT}=-\sum_{\langle i,j\rangle} (H+J\langle S_i\rangle_t)S_j\xrightarrow{m_i=m}-\underbrace{(H+zJ m)}_{H_{eff}}\sum_jS_j\text{.}
$$

在最後一個式子中，我們又進一步假設 $m_i$ 與位置無關，並把它寫成 $m$。如果再盯著最後這個結果看，就會發現：它其實又變成了一個只有「外加」磁場的非交互作用自旋系統。

此時，我們對試探分佈函數其實已經加上了隱含條件：它必須產生我們想要的磁化值 $m$。另一方面，由於這個系統看起來就是一個處在有效磁場 $(H+zJm)$ 下的非交互作用自旋系統，我們也知道對應的分佈函數會由這個有效磁場參數化。於是，自洽條件就出現了。我們實際上是在問：在哪個 $m$ 值下，由 $H+zJm$ 所參數化的試探分佈函數 $P_t(\{S_i\})$，其單自旋期望值也恰好等於 $m$？而這個系統單自旋的期望值就是 $\tanh\left[\beta(H+zJm)\right]$。因此，自洽方程為

$$
m=\tanh\left[\beta(H+zJm)\right]\text{.}
$$

這個方程的質性行為只是簡單的計算問題，所以留作練習。

從邏輯上看，我們在這裡做了幾個假設：
1. 「漲落」很小：$\langle (S_i-\langle S_i\rangle_t)\rangle_E\ll1$
2. 平均場參數 $m_i$ 在空間上均勻。
3. 我們能自洽地解這個方程。

*在這個簡單問題裡，我們也可以看到平均場理論隱含地假設分佈函數可因式分解，也就是 $P_t(\{S_i\})=\prod_iP_{t,i}(S_i)$。*

滿足自洽方程是平均場理論成立的必要條件，但不是充分條件。問題在於：就算我們找到一個滿足自洽方程的試探分佈函數，也不代表漲落真的很小。更重要的邏輯問題是：就算能夠推導出自洽的試探分佈函數，也不保證這個試探分佈函數在質性上抓住了精確分佈函數的物理圖像。

因此，平均場理論是一種通用且簡單的方法，可以把物理圖像寫成數學形式。不過，它也受到上述限制。

## 變分平均場理論

Weiss 平均場理論的物理圖像很清楚。不過，平均場理論背後更一般的結構未必那麼清楚。因此，這裡我會介紹另一種建立平均場理論的方法，也就是變分平均場理論。

這個方法依賴下列不等式

$$
\langle e^{f(x)}\rangle\ge e^{\langle f(x)\rangle}\text{.}
$$(exp_convex)

證明並不困難，所以留作練習。

現在從配分函數開始：

$$
Z=\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]+H_0(\{S_i\})\right\}}\text{.}
$$

這裡 $H_{\Omega}$ 是我們想要求解的交互作用哈密頓量，$H_0$ 是我們已知其行為的非交互作用試探哈密頓量。這同樣只是重寫而已。現在，我們可以把它改寫成

$$
Z=Z_0\sum_{\{S_i\}} e^{-\beta \left\{\left[H_{\Omega}(\{S_i\})-H_0(\{S_i\})\right]\right\}} \left[\frac{e^{-\beta H_0(\{S_i\})}}{Z_0}\right]=\langle e^{-\beta(H_{\Omega}-H_0)}\rangle_0
$$

其中

$$
Z_0=\sum_{\{S_i\}}e^{-\beta H_0(\{S_i\})}=e^{-\beta F_0}=e^{-\beta(\langle H_0\rangle_0-TS_0)}\text{.}
$$

這裡 $\langle \rangle_0$ 表示以試探哈密頓量 $H_0$ 所生成之正則系綜機率分佈來做平均。利用 [inequlity](exp_convex)，我們有

$$
Z\ge Z_0 e^{-\beta\langle H_{\Omega}-H_0\rangle_0}\equiv Z_{MFT}
$$

這個方法的想法是：我們想找出一個 $H_0$，使得 $Z_{MFT}$ 最大。等價地，就是希望最小化 $F_{MFT}\equiv -k_BT \ln Z_{MFT}$。

根據定義，我們可以得到

$$
f_{MFT}=N(\Omega)^{-1}F_{MFT}=N(\Omega)^{-1}(\langle H_{\Omega}\rangle_0-TS_0)\text{.}
$$

注意，交互作用哈密頓量 $H_{\Omega}$ 的期望值是用非交互作用試探哈密頓量 $H_0$ 所對應的分佈函數來計算的。一旦我們把平均場自由能寫成試探哈密頓量 $H_0$ 的變分參數函數，就可以對這個變分參數取極小，並導出自洽方程。

```{admonition} What?
:class: tip
我們這裡使用的方法，是以「序參量」 $m$ 為變分變數。不過還有一種更一般的方法，可以把試探哈密頓量對應的機率分佈本身視為變分函數，直接找出變分極小值。第二種方法更一般，但限於時間，這裡不介紹。有興趣的讀者可參考 {cite:p}`chaikin1995principles`。
```

現在就用簡單的 Ising 模型來看它如何運作。

我們選擇一個具有變分參數 $\lambda$ 的試探哈密頓量

$$
H_0(\lambda)=-\lambda\sum_iS_i\text{.}
$$

根據我們對這個系統的了解，磁化 $m$ 與變分參數 $\lambda$ 之間具有一一對應關係。因此後面我們會直接對 $m$ 做變分。

根據定義，

$$
\langle S_i\rangle_0\equiv m=\frac{N_{\uparrow}-N_{\downarrow}}{N(\Omega)}\text{.}
$$

而且我們知道，$H_0$ 對應的機率分佈函數是可以因式分解的。

利用這些資訊，我們可以很容易地寫出 $\langle H_{\Omega}\rangle_0$：

$$
\langle H_{\Omega}\rangle_0=-J\sum_{\langle i,j\rangle_0 } \langle S_iS_j\rangle_0-H\sum_i\langle S_i\rangle_0=-J\sum_{\langle i,j\rangle} \langle S_i\rangle_0\langle S_j\rangle_0-H\sum_i\langle S_i\rangle_0\\
=N(\Omega)\left[-Jm^2\frac{z}{2}-Hm\right]
$$

當 $\langle S_i\rangle_0=m$ 時，熵為

$$
S_0=k_B\ln C^N_{N_{\uparrow}}\xrightarrow{\text{Stirling 近似}}=N(\Omega)k_B\left\{\ln 2-\frac{1}{2}\left[(1+m)\ln(1+m)+(1-m)\ln(1-m)\right]\right\}\text{.}
$$

利用上面的結果，我們就可以建立自由能密度 $f(T,m)$。接著對 $m$ 取極小，也就是要求 $\frac{df}{dm}=0$：

$$
\frac{df}{dm}=-Jzm-H +k_BT\underbrace{\left[\frac{1}{2}\ln\left(\frac{1+m}{1-m}\right)\right]}_{\tanh^{-1} m}=0\text{.}
$$

因此，我們得到自洽方程

$$
m=\tanh\left[\beta(Jzm+H)\right]\text{.}
$$
