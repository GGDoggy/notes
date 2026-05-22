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

依照你最新指定的寫法，以下將 pair-correlation function 的分解視為新的定義：
$$
\begin{align}
g(r,\theta_1,\theta_2)
&=
\sum_{n_1,n_2}
B(n_1,n_2,r)\cos(n_1\theta_1+n_2\theta_2)\\
&=\sum_{n_1,n_2}
B_s(n_1,n_2,r)\cos(n_1\theta_1)\cos(n_2\theta_2)+B_a(n_1,n_2,r)\sin(n_1\theta_1)\sin(n_2\theta_2)
\end{align}
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

並把它拆成實部與虛部

$$
C(n,m,q)=C_R(n,m,q)+i\,C_I(n,m,q),
$$

由於 $\cos^n\theta\,\sin^m\theta$ 為實函數，還有

$$
C(n,m,-q)=C(n,m,q)^*
=
C_R(n,m,q)-i\,C_I(n,m,q).
$$

則由

$$
\cos\theta\,e^{iq\theta}
=
\frac{1}{2}\left(e^{i(q+1)\theta}+e^{i(q-1)\theta}\right),
$$

$$
\sin\theta\,e^{iq\theta}
=
\frac{1}{2i}\left(e^{i(q+1)\theta}-e^{i(q-1)\theta}\right),
$$

可得移位關係

$$
C(n+1,m,q)
=
\frac{1}{2}\Bigl[
C(n,m,q+1)+C(n,m,q-1)
\Bigr],
$$

$$
C(n,m+1,q)
=
\frac{1}{2i}\Bigl[
C(n,m,q+1)-C(n,m,q-1)
\Bigr].
$$

因此

$$
\widetilde{\mathbf C}_{nm}(q)
=
\frac{1}{2\pi}
\Bigl[
\hat u\Bigl(C(n,m,q+1)+C(n,m,q-1)\Bigr)
-i\hat v\Bigl(C(n,m,q+1)-C(n,m,q-1)\Bigr)
\Bigr],
$$

## 5. 徑向積分與最終局域形式

把徑向積分單獨提出來。為了對應上一節使用的
$B_s$ 與 $B_a$ 分解，先定義

$$
A_s(n,m,n_1,n_2)
:=
\int_0^\infty dr\;
r^{n+m+1}U'(r)\,B_s(n_1,n_2,r),
$$

$$
A_a(n,m,n_1,n_2)
:=
\int_0^\infty dr\;
r^{n+m+1}U'(r)\,B_a(n_1,n_2,r).
$$

接下來分別處理 $B_s$ 與 $B_a$ 兩部分。
先看 $\theta_2$ 積分。由

$$
\cos(n_2\theta_2)=\frac{e^{in_2\theta_2}+e^{-in_2\theta_2}}{2},
\qquad
\sin(n_2\theta_2)=\frac{e^{in_2\theta_2}-e^{-in_2\theta_2}}{2i},
$$

可得

$$
\int_0^{2\pi}d\theta_2\;e^{ik\theta_2}\cos(n_2\theta_2)
=
\pi\bigl(\delta_{k,n_2}+\delta_{k,-n_2}\bigr),
$$

$$
\int_0^{2\pi}d\theta_2\;e^{ik\theta_2}\sin(n_2\theta_2)
=
i\pi\bigl(\delta_{k,n_2}-\delta_{k,-n_2}\bigr).
$$

因此在保留 $e^{ik\phi}$ 之後，
$B_s$ 部分對應的 $\theta_2$ 積分給出

$$
\pi\left[
\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
+
\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
\right],
$$

而 $B_a$ 部分則給出

$$
i\pi\left[
\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
-
\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
\right].
$$

再看 $\theta_1$ 積分。由上一節
$\widetilde{\mathbf C}_{nm}(q)$ 的定義與
$C(n,m,q)$ 的表示式可知。再利用
$C(n,m,-q)=C(n,m,q)^*$，可把
$q=\pm n_1$ 的組合整理成只含
$C_R,C_I$ 與 $n_1\pm1$ 的形式：

$$
\int_0^{2\pi}d\theta_1\,
\Bigl(\cos\theta_1\,\hat u+\sin\theta_1\,\hat v\Bigr)
\cos^n\theta_1\,\sin^m\theta_1\,\cos(n_1\theta_1)
=
\frac{1}{\pi}
\Bigl[
\hat u\!\left(
\frac{C_R(n,m,n_1+1)+C_R(n,m,n_1-1)}{2}
\right)
+
\hat v\!\left(
\frac{C_I(n,m,n_1+1)-C_I(n,m,n_1-1)}{2}
\right)
\Bigr],
$$

以及

$$
\int_0^{2\pi}d\theta_1\,
\Bigl(\cos\theta_1\,\hat u+\sin\theta_1\,\hat v\Bigr)
\cos^n\theta_1\,\sin^m\theta_1\,\sin(n_1\theta_1)
=
\frac{1}{\pi}
\Bigl[
\hat u\!\left(
\frac{C_I(n,m,n_1+1)+C_I(n,m,n_1-1)}{2}
\right)
-
\hat v\!\left(
\frac{C_R(n,m,n_1+1)-C_R(n,m,n_1-1)}{2}
\right)
\Bigr].
$$

把徑向積分、$\theta_2$ 積分與 $\theta_1$ 積分全部合併後，
$\mathbf I[\rho]$ 就可以完全寫成 $\hat u,\hat v$ 基底下的局域形式：

$$
\boxed{
\begin{aligned}
\mathbf I[\rho]
=\;&
\frac{1}{2}\sum_{n,m,n_1,n_2}
A_s(n,m,n_1,n_2)
\Bigl[
\hat u\!\left(
\frac{C_R(n,m,n_1+1)+C_R(n,m,n_1-1)}{2}
\right)
+
\hat v\!\left(
\frac{C_I(n,m,n_1+1)-C_I(n,m,n_1-1)}{2}
\right)
\Bigr]
\left[
\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
+
\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
\right]
\\[0.5em]
&+
\frac{1}{2}\sum_{n,m,n_1,n_2}
A_a(n,m,n_1,n_2)
\Bigl[
\hat u\!\left(
\frac{C_I(n,m,n_1+1)+C_I(n,m,n_1-1)}{2}
\right)
-
\hat v\!\left(
\frac{C_R(n,m,n_1+1)-C_R(n,m,n_1-1)}{2}
\right)
\Bigr]
\left[
\bigl(D_{nm}\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
-
\bigl(D_{nm}\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
\right].
\end{aligned}
}
$$

這個式子已經不再使用壓縮記號 $A(n,m,n_1,n_2)$，
也不再使用 $\widetilde{\mathbf C}_{nm}(q)$；
所有角向結構都已明確展開成
$C_R(n,m,n_1\pm1)$、$C_I(n,m,n_1\pm1)$
與局部基底 $(\hat u,\hat v)$ 的線性組合。

### 5.5 把共軛對改寫成 $\cos$ 與 $\sin$

若先只看未經微分的 Fourier mode，寫成

$$
\rho_{n_2}(\mathbf r,t)
=
X_{n_2}(\mathbf r,t)e^{i\psi_{n_2}(\mathbf r,t)},
\qquad
\rho_{-n_2}(\mathbf r,t)
=
X_{n_2}(\mathbf r,t)e^{-i\psi_{n_2}(\mathbf r,t)},
$$

則

$$
\bigl(\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
+
\bigl(\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
=
X_{n_2}e^{-i(n_2\phi+\psi_{n_2})}
+
X_{n_2}e^{+i(n_2\phi+\psi_{n_2})}
=
2X_{n_2}\cos\!\bigl(n_2\phi+\psi_{n_2}\bigr),
$$

而反對稱組合則是

$$
\bigl(\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
-
\bigl(\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
=
X_{n_2}e^{+i(n_2\phi+\psi_{n_2})}
-
X_{n_2}e^{-i(n_2\phi+\psi_{n_2})}
=
2iX_{n_2}\sin\!\bigl(n_2\phi+\psi_{n_2}\bigr).
$$

因此若某一步尚未讓 $D_{nm}$ 作用到 Fourier mode 上，
那麼 $B_s$ 部分自然對應到 $\cos(n_2\phi+\psi_{n_2})$，
而 $B_a$ 部分自然對應到 $\sin(n_2\phi+\psi_{n_2})$。

若保留目前推導中的微分算子，則只要注意
$D_{nm}$ 只對 $\mathbf r$ 作用，
而 $e^{\pm in_2\phi}$ 對它而言是常數因子，因此

$$
\bigl(D_{nm}\rho_{-n_2}\bigr)e^{-in_2\phi}
+
\bigl(D_{nm}\rho_{n_2}\bigr)e^{+in_2\phi}
=
D_{nm}\!\left[
\bigl(\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
+
\bigl(\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
\right],
$$

$$
\bigl(D_{nm}\rho_{n_2}\bigr)e^{+in_2\phi}
-
\bigl(D_{nm}\rho_{-n_2}\bigr)e^{-in_2\phi}
=
D_{nm}\!\left[
\bigl(\rho_{n_2}(\mathbf r,t)\bigr)e^{+in_2\phi}
-
\bigl(\rho_{-n_2}(\mathbf r,t)\bigr)e^{-in_2\phi}
\right].
$$

再代入前面已得到的三角形式，就有

$$
\bigl(D_{nm}\rho_{-n_2}\bigr)e^{-in_2\phi}
+
\bigl(D_{nm}\rho_{n_2}\bigr)e^{+in_2\phi}
=
2D_{nm}\!\left[
X_{n_2}(\mathbf r,t)\cos\!\bigl(n_2\phi+\psi_{n_2}(\mathbf r,t)\bigr)
\right],
$$

$$
\bigl(D_{nm}\rho_{n_2}\bigr)e^{+in_2\phi}
-
\bigl(D_{nm}\rho_{-n_2}\bigr)e^{-in_2\phi}
=
2iD_{nm}\!\left[
X_{n_2}(\mathbf r,t)\sin\!\bigl(n_2\phi+\psi_{n_2}(\mathbf r,t)\bigr)
\right].
$$

所以目前第 5 節最後那個 boxed 公式，也可以等價地改寫為

$$
\boxed{
\begin{aligned}
\mathbf I[\rho]
=\;&
\sum_{n,m,n_1,n_2}
A_s(n,m,n_1,n_2)
\Bigl[
\hat u\!\left(
\frac{C_R(n,m,n_1+1)+C_R(n,m,n_1-1)}{2}
\right)
+
\hat v\!\left(
\frac{C_I(n,m,n_1+1)-C_I(n,m,n_1-1)}{2}
\right)
\Bigr]
\,D_{nm}\!\left[
X_{n_2}(\mathbf r,t)\cos\!\bigl(n_2\phi+\psi_{n_2}(\mathbf r,t)\bigr)
\right]
\\[0.5em]
&+
i\sum_{n,m,n_1,n_2}
A_a(n,m,n_1,n_2)
\Bigl[
\hat u\!\left(
\frac{C_I(n,m,n_1+1)+C_I(n,m,n_1-1)}{2}
\right)
-
\hat v\!\left(
\frac{C_R(n,m,n_1+1)-C_R(n,m,n_1-1)}{2}
\right)
\Bigr]
\,D_{nm}\!\left[
X_{n_2}(\mathbf r,t)\sin\!\bigl(n_2\phi+\psi_{n_2}(\mathbf r,t)\bigr)
\right].
\end{aligned}
}
$$

這樣寫不需要另外定義新的振幅與相位符號，
而且完整保留了 $D_{nm}$ 對整個
$X_{n_2}\cos(\cdots)$ 或 $X_{n_2}\sin(\cdots)$ 的作用。
