# Results.md 的驗證與推導

這份推導採用你指定的角變數與局部基底：

$$
\theta_1=\psi_R-\phi,\qquad \theta_2=\phi'-\phi,
$$

$$
\hat u=\hat{\mathbf u}(\phi),\qquad
\hat v=\hat{\mathbf u}\!\left(\phi+\frac{\pi}{2}\right),
\qquad
\hat{\mathbf u}(\psi_R)=(\cos\psi_R,\sin\psi_R)^T.
$$

我們要處理的是

$$
\mathbf I[\rho](\mathbf r,\phi,t)
=
\int_0^\infty dr\int_0^{2\pi}d\psi_R\int_0^{2\pi}d\phi'\;
r\,U'(r)\,\hat{\mathbf u}(\psi_R)\,
g(r,\psi_R-\phi,\phi'-\phi)\,
\rho(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t).
$$

## 1. 先固定 $g$ 的分解

依照你最新指定的寫法，先把 pair-correlation function 展開成

$$
g(r,\theta_1,\theta_2)
=
\sum_{n_1,n_2}
B(n_1,n_2,r)\cos(n_1\theta_1+n_2\theta_2).
$$

再把 cosine 改寫成指數形式：

$$
\cos(n_1\theta_1+n_2\theta_2)
=
\frac{1}{2}
\left[
e^{i(n_1\theta_1+n_2\theta_2)}
+
e^{-i(n_1\theta_1+n_2\theta_2)}
\right].
$$

因此

$$
g(r,\theta_1,\theta_2)
=
\sum_{n_1,n_2}\frac{B(n_1,n_2,r)}{2}
\left[
e^{i(n_1\theta_1+n_2\theta_2)}
+
e^{-i(n_1\theta_1+n_2\theta_2)}
\right].
$$

## 2. 對局部基底做 Taylor 展開

因為

$$
\psi_R=\theta_1+\phi,
$$

所以

$$
\hat{\mathbf u}(\psi_R)
=
\cos(\psi_R-\phi)\,\hat u+\sin(\psi_R-\phi)\,\hat v
=
\cos\theta_1\,\hat u+\sin\theta_1\,\hat v,
$$

以及

$$
r\hat{\mathbf u}(\psi_R)=r\cos\theta_1\,\hat u+r\sin\theta_1\,\hat v.
$$

定義方向導數

$$
\partial_u:=\hat u\cdot\nabla,\qquad
\partial_v:=\hat v\cdot\nabla,
$$

與微分算子

$$
D_{nm}:=\frac{1}{n!\,m!}\partial_u^n\partial_v^m.
$$

則密度在 $\mathbf r$ 附近可寫成

$$
\rho\bigl(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t\bigr)
=
\sum_{n,m\ge 0}
r^{n+m}\cos^n\theta_1\,\sin^m\theta_1\,
D_{nm}\rho(\mathbf r,\phi',t).
$$

再對角度 $\phi'$ 做 Fourier 展開：

$$
\rho(\mathbf r,\phi,t)=\sum_{k\in\mathbb Z}\rho_k(\mathbf r,t)e^{ik\phi}.
$$

因此

$$
\rho\bigl(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t\bigr)
=
\sum_{n,m\ge0}\sum_{k\in\mathbb Z}
r^{n+m}\cos^n\theta_1\,\sin^m\theta_1\,
\bigl(D_{nm}\rho_k(\mathbf r,t)\bigr)e^{ik\phi'}.
$$

## 3. 先做 $\theta_2$ 積分

由

$$
\theta_2=\phi'-\phi,\qquad
\phi'=\theta_2+\phi,\qquad
d\phi'=d\theta_2,
$$

可得

$$
e^{ik\phi'}=e^{ik(\theta_2+\phi)}=e^{ik\phi}e^{ik\theta_2}.
$$

把第 1 節的 $g$ 分解與第 2 節的密度展開一起代入後，
$\theta_2$ 只會出現在

$$
e^{ik\theta_2}e^{+in_2\theta_2}
\qquad\text{或}\qquad
e^{ik\theta_2}e^{-in_2\theta_2}.
$$

因此

$$
\int_0^{2\pi}d\theta_2\;e^{ik\theta_2}e^{+in_2\theta_2}
=
2\pi\,\delta_{k,-n_2},
$$

$$
\int_0^{2\pi}d\theta_2\;e^{ik\theta_2}e^{-in_2\theta_2}
=
2\pi\,\delta_{k,n_2}.
$$

連同 $e^{ik\phi}$ 一起保留時，得到

$$
\int_0^{2\pi}d\theta_2\;e^{ik(\theta_2+\phi)}e^{+in_2\theta_2}
=
2\pi\,\delta_{k,-n_2}\,e^{-in_2\phi},
$$

$$
\int_0^{2\pi}d\theta_2\;e^{ik(\theta_2+\phi)}e^{-in_2\theta_2}
=
2\pi\,\delta_{k,n_2}\,e^{+in_2\phi}.
$$

所以 $\theta_2$ 積分之後，留下的兩項是

$$
e^{+in_1\theta_1}\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi},
\qquad
e^{-in_1\theta_1}\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}.
$$

若 $\rho$ 為實函數，則

$$
\rho_{-n_2}=\rho_{n_2}^*,
\qquad
D_{nm}\rho_{-n_2}=\bigl(D_{nm}\rho_{n_2}\bigr)^*.
$$

## 4. 再做 $\theta_1$ 積分

因為

$$
\hat{\mathbf u}(\psi_R)=\cos\theta_1\,\hat u+\sin\theta_1\,\hat v,
$$

定義純 $\theta_1$ 角積分

$$
\widetilde{\mathbf C}_{nm}(q)
:=
\int_0^{2\pi}d\theta_1\,
\Bigl(\cos\theta_1\,\hat u+\sin\theta_1\,\hat v\Bigr)
\cos^n\theta_1\,\sin^m\theta_1\,e^{iq\theta_1}.
$$

這個積分本身不會再產生額外的 $e^{iq\phi}$。
在目前的推導裡，$\theta_1$ 積分只留下
$\widetilde{\mathbf C}_{nm}(q)$；
$\phi$ 依賴一部分已經在 $\theta_2$ 積分時變成
$e^{\pm in_2\phi}$，另一部分則保留在
$\hat u=\hat{\mathbf u}(\phi)$ 與
$\hat v=\hat{\mathbf u}(\phi+\pi/2)$ 這組局部基底裡。

把向量分量拆開，得到

$$
\widetilde{\mathbf C}_{nm}(q)
=
\hat u\int_0^{2\pi}d\theta_1\,
\cos^{n+1}\theta_1\,\sin^m\theta_1\,e^{iq\theta_1}
+
\hat v\int_0^{2\pi}d\theta_1\,
\cos^n\theta_1\,\sin^{m+1}\theta_1\,e^{iq\theta_1}.
$$

若定義純量積分

$$
C(n,m,q):=
\pi\int_0^{2\pi}\cos^n\theta\,\sin^m\theta\,e^{iq\theta}\,d\theta,
$$

則

$$
\widetilde{\mathbf C}_{nm}(q)
=
\frac{1}{\pi}
\Bigl[
\hat u\,C(n+1,m,q)+\hat v\,C(n,m+1,q)
\Bigr],
$$

## 5. 徑向積分與最終局域形式

把徑向積分單獨提出來，定義

$$
A(n,m,n_1,n_2)
:=
\int_0^\infty dr\;
r^{n+m+1}U'(r)\,B(n_1,n_2,r).
$$

綜合第 1 到第 4 節，可得

$$
\boxed{
\mathbf I[\rho]
=
\pi\sum_{n,m,n_1,n_2}
A(n,m,n_1,n_2)
\left[
\widetilde{\mathbf C}_{nm}(n_1)\,
\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
+
\widetilde{\mathbf C}_{nm}(-n_1)\,
\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
\right].
}
$$

這裡顯式寫出的相位只來自 $\theta_2$ 積分留下的
$e^{\pm in_2\phi}$。其餘的 $\phi$ 依賴仍然包在
$\widetilde{\mathbf C}_{nm}(q)$ 所使用的局部基底
$(\hat u,\hat v)$ 裡。接下來先把
$\rho_{-n_2}e^{-in_2\phi}$ 與 $\rho_{n_2}e^{+in_2\phi}$
這對共軛項合併，看看是否能對 $n_2$ 的求和整理回 $\rho$ 的形式。

### 5.5 合併共軛項

在進入 Results.md 的整理寫法之前，先把
$\rho_{-n_2}e^{-in_2\phi}$ 和
$\rho_{n_2}e^{+in_2\phi}$ 這對共軛項合併。

先把 Fourier mode 寫成振幅與相位：
$$
\rho_{n_2}(\mathbf r,t)
=
X_{n_2}(\mathbf r,t)e^{i\psi_{n_2}(\mathbf r,t)},
\qquad
\rho_{-n_2}(\mathbf r,t)
=
X_{n_2}(\mathbf r,t)e^{-i\psi_{n_2}(\mathbf r,t)}.
$$

再把徑向積分與角向積分得到的複係數拆成實部與虛部：
$$
\pi A(n,m,n_1,n_2)\,C(n+1,m,n_1)
=
C_R(n+1,m)+i\,C_I(n+1,m),
$$
$$
\pi A(n,m,n_1,n_2)\,C(n,m+1,n_1)
=
C_R(n,m+1)+i\,C_I(n,m+1).
$$

令
$$
\Theta:=n_2\phi+\psi_{n_2},
\qquad
Z_u:=\pi A\,C(n+1,m,n_1),
\qquad
Z_v:=\pi A\,C(n,m+1,n_1).
$$

則 $\hat u$ 分量中的共軛對可寫成
$$
Z_u^*X_{n_2}e^{-i\Theta}+Z_uX_{n_2}e^{+i\Theta}
=
2X_{n_2}\Bigl[
C_R(n+1,m)\cos\Theta
-C_I(n+1,m)\sin\Theta
\Bigr],
$$
而 $\hat v$ 分量同理為
$$
Z_v^*X_{n_2}e^{-i\Theta}+Z_vX_{n_2}e^{+i\Theta}
=
2X_{n_2}\Bigl[
C_R(n,m+1)\cos\Theta
-C_I(n,m+1)\sin\Theta
\Bigr].
$$

因此若定義
$$
\mathbf C_R
:=
C_R(n+1,m)\,\hat u+C_R(n,m+1)\,\hat v,
\qquad
\mathbf C_I
:=
C_I(n+1,m)\,\hat u+C_I(n,m+1)\,\hat v,
$$
那麼每一組 $(n,m,n_1,n_2)$ 的貢獻都可以整理成
$$
2X_{n_2}\Bigl[
\cos\Theta\,\mathbf C_R
-\sin\Theta\,\mathbf C_I
\Bigr].
$$

## 6. Results.md 的整理寫法
若只是想整理成你圖中的「振幅乘上正弦/餘弦，再乘上向量係數」的版型，
那麼最直接且和上面推導一致的寫法是
$$
\mathbf I
=
\sum_{n,m,n_1,n_2}
D_{nm}X_{n_2}
\Bigl[
2\cos(n_2\phi+\psi_{n_2})\,\mathbf C_R
-2\sin(n_2\phi+\psi_{n_2})\,\mathbf C_I
\Bigr].
$$

若你一定要保留 `A_s`、`A_0` 這種符號，也可以等價地定義
$$
A_0:=2,
\qquad
A_s:=-2,
$$
於是
$$
\mathbf I
=
\sum_{n,m,n_1,n_2}
D_{nm}X_{n_2}
\Bigl[
A_s\sin(n_2\phi+\psi_{n_2})
\bigl(
C_I(n+1,m)\,\hat u+C_I(n,m+1)\,\hat v
\bigr)
+
A_0\cos(n_2\phi+\psi_{n_2})
\bigl(
C_R(n+1,m)\,\hat u+C_R(n,m+1)\,\hat v
\bigr)
\Bigr].
$$

但在你現在指定的
$g(r,\theta_1,\theta_2)=\sum B(n_1,n_2,r)\cos(n_1\theta_1+n_2\theta_2)$
分解下，至少有三個結構不能直接被這樣壓掉：

1. 顯式相位只直接留下 $e^{\pm in_2\phi}$；其餘 $\phi$ 依賴藏在
   $(\hat u,\hat v)$ 這組旋轉基底裡，所以不能簡單壓成只看一個
   $n_2\phi$ 的純量正弦。
2. 係數仍然是向量結構，必須保留 $\widetilde{\mathbf C}_{nm}$，不能直接縮成單一純量振幅。
3. 導數先作用在 $\rho_{n_2}$ 上，所以真正該取相位的是
   $D_{nm}\rho_{n_2}$，不是直接用 $\arg(\rho_{n_2})$。

## 7. 若只看某個固定方向分量

例如只看 $\hat u$ 分量，可以取

$$
K_u^{(+)}:=A(n,m,n_1,n_2)\,\hat u\cdot\widetilde{\mathbf C}_{nm}(n_1),
\qquad
K_u^{(-)}:=A(n,m,n_1,n_2)\,\hat u\cdot\widetilde{\mathbf C}_{nm}(-n_1).
$$

再寫成極形式

$$
K_u^{(+)}=|K_u^{(+)}|e^{i\delta_u^{(+)}},
\qquad
D_{nm}\rho_{n_2}=|D_{nm}\rho_{n_2}|e^{i\chi_{nm,n_2}},
$$

則對應項會變成

$$
2\pi |K_u^{(-)}|\,|D_{nm}\rho_{n_2}|
\cos\!\bigl(n_2\phi-\delta_u^{(-)}-\chi_{nm,n_2}\bigr),
$$

或等價地用另一支共軛項來寫。這再次說明相位來自
$K$ 與 $D_{nm}\rho_{n_2}$ 的組合，而不是單獨來自 $\rho_{n_2}$。

## 8. 結論

Results.md 的整體策略仍然是對的：

- 先把 $g$ 展成角向 harmonic。
- 再把空間位移做 Taylor 展開。
- 再把 $\rho$ 對 $\phi'$ 做 Fourier 展開。
- 最後用角積分挑出保留的 mode。

但只要起始分解改成
$\cos(n_1\theta_1+n_2\theta_2)$，
最後的局域結果就應該使用第 5 節的 boxed 公式，而不是舊版
$A_s,A_a$，也不能把整個向量結果直接壓成單一
$\sin(n_2\phi+\cdots)$ 的純量寫法。
