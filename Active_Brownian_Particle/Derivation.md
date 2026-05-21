# `Results.md` 的驗證與推導

## 1. 起點

我們從下式出發：

$$
\mathbf I[\rho](\mathbf r,\phi,t)
=
\int_0^\infty dr \int_0^{2\pi} d\psi_R \int_0^{2\pi} d\phi'\;
r\,U'(r)\,\hat{\mathbf u}(\psi_R)\,
g\bigl(r,\psi_R-\phi,\phi'-\phi\bigr)\,
\rho\bigl(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t\bigr),
$$

其中

$$
\hat{\mathbf u}(\psi_R)=(\cos\psi_R,\sin\psi_R)^T.
$$

以下使用縮寫

$$
\theta_1=\psi_R-\phi,\qquad \theta_2=\phi'-\phi.
$$

`Results.md` 中對 pair-correlation function 的展開寫成

$$
g(r,\theta_1,\theta_2)
=
\sum_{n_1,n_2}
\Bigl[
B_s(n_1,n_2,r)\cos(n_1\theta_1)\cos(n_2\theta_2)
+
B_a(n_1,n_2,r)\sin(n_1\theta_1)\sin(n_2\theta_2)
\Bigr].
$$

## 2. 沿著 $\hat u,\hat v$ 的 Taylor 展開

這裡不使用固定的 $x,y$ 座標，而改用隨粒子方向 $\phi$ 轉動的局部正交基底

$$
\hat u=\hat{\mathbf u}(\phi),\qquad
\hat v=\hat{\mathbf u}\!\left(\phi+\frac{\pi}{2}\right).
$$

由於

$$
\hat{\mathbf u}(\psi_R)
=
\cos(\psi_R-\phi)\,\hat u+\sin(\psi_R-\phi)\,\hat v
=
\cos\theta_1\,\hat u+\sin\theta_1\,\hat v,
$$

因此位移向量可以寫成

$$
r\hat{\mathbf u}(\psi_R)=r\cos\theta_1\,\hat u+r\sin\theta_1\,\hat v.
$$

令方向導數記為

$$
\partial_u:=\hat u\cdot\nabla,\qquad
\partial_v:=\hat v\cdot\nabla.
$$

則位移後的密度在 $\mathbf r$ 附近的 Taylor 展開為

$$
\rho\bigl(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t\bigr)
=
\sum_{n,m\ge 0}
\frac{r^{n+m}}{n!\,m!}
\cos^n\theta_1\,\sin^m\theta_1\,
\partial_u^n\partial_v^m \rho(\mathbf r,\phi',t).
$$

接著把 $\rho$ 對角度 $\phi$ 做 Fourier 展開：

$$
\rho(\mathbf r,\phi,t)=\sum_{k\in\mathbb Z}\rho_k(\mathbf r,t)e^{ik\phi},
\qquad
\rho_{-k}=\rho_k^*
$$

因為 $\rho$ 是實函數，所以滿足 $\rho_{-k}=\rho_k^*$。定義

$$
D_{nm}^{(k)}(\mathbf r,t;\phi)
:=
\frac{1}{n!\,m!}\partial_u^n\partial_v^m\rho_k(\mathbf r,t).
$$

則可寫成

$$
\rho\bigl(\mathbf r+r\hat{\mathbf u}(\psi_R),\phi',t\bigr)
=
\sum_{n,m\ge 0}\sum_{k\in\mathbb Z}
r^{n+m}\cos^n\theta_1\,\sin^m\theta_1\,
D_{nm}^{(k)}(\mathbf r,t;\phi)e^{ik\phi'}.
$$

## 3. 角向 kernel 的指數形式

令

$$
A=n_1(\psi_R-\phi)=n_1\theta_1,\qquad B=n_2(\phi'-\phi)=n_2\theta_2.
$$

利用

$$
\cos A\cos B=\frac{1}{4}\left(e^{i(A+B)}+e^{i(A-B)}+e^{-i(A-B)}+e^{-i(A+B)}\right),
$$

以及

$$
\sin A\sin B=\frac{1}{4}\left(-e^{i(A+B)}+e^{i(A-B)}+e^{-i(A-B)}-e^{-i(A+B)}\right),
$$

可得

$$
\begin{aligned}
&B_s\cos A\cos B + B_a\sin A\sin B
\\
&=
\frac{B_s-B_a}{4}\left(e^{i(A+B)}+e^{-i(A+B)}\right)
+
\frac{B_s+B_a}{4}\left(e^{i(A-B)}+e^{-i(A-B)}\right).
\end{aligned}
$$

這個式子最清楚地顯示了最後會保留下來的角向 harmonic 結構。

## 4. 對 $\theta_2$ 的積分

由於

$$
\theta_2=\phi'-\phi,
\qquad
\phi'=\theta_2+\phi,
\qquad
d\phi'=d\theta_2,
$$

所以把 $\rho$ 的 Fourier 展開代入後，可以直接改成對 $\theta_2$ 積分。此時

$$
e^{ik\phi'}=e^{ik(\theta_2+\phi)}=e^{ik\phi}e^{ik\theta_2}.
$$

因此只需要處理形如

$$
\int_0^{2\pi} d\theta_2\; e^{ik\theta_2}e^{+in_2\theta_2}
=
2\pi\,\delta_{k,-n_2},
$$

以及

$$
\int_0^{2\pi} d\theta_2\; e^{ik\theta_2}e^{-in_2\theta_2}
=
2\pi\,\delta_{k,n_2}
$$

的正交關係。

把前面的相位因子一併乘回去後，就得到

$$
\int_0^{2\pi} d\theta_2\; e^{ik(\theta_2+\phi)}e^{+in_2\theta_2}
=
2\pi\,\delta_{k,-n_2}\,e^{-in_2\phi},
$$

$$
\int_0^{2\pi} d\theta_2\; e^{ik(\theta_2+\phi)}e^{-in_2\theta_2}
=
2\pi\,\delta_{k,n_2}\,e^{+in_2\phi}.
$$

因此，$\theta_2$ 積分後自然出現的密度模態是

$$
D_{nm}^{(n_2)}(\mathbf r,t;\phi)
\qquad\text{與}\qquad
D_{nm}^{(-n_2)}(\mathbf r,t;\phi)
=
\bigl(D_{nm}^{(n_2)}(\mathbf r,t;\phi)\bigr)^*.
$$

## 5. 對 $\psi_R$ 的積分與向量係數

由於 Taylor 展開已經改寫成 $\theta_1$ 的形式，現在自然出現的向量角積分是

$$
\mathbf C_{nm}(q;\phi)
:=
\int_0^{2\pi} d\psi_R\;
\hat{\mathbf u}(\psi_R)\cos^n\theta_1\,\sin^m\theta_1\,e^{iq\psi_R}.
$$

把

$$
\hat{\mathbf u}(\psi_R)=\cos\theta_1\,\hat u+\sin\theta_1\,\hat v,
\qquad
e^{iq\psi_R}=e^{iq\phi}e^{iq\theta_1}
$$

代入，可得

$$
\begin{aligned}
\mathbf C_{nm}(q;\phi)
=
e^{iq\phi}\int_0^{2\pi} d\theta_1\,
\Bigl(\cos\theta_1\,\hat u+\sin\theta_1\,\hat v\Bigr)
\cos^n\theta_1\,\sin^m\theta_1\,e^{iq\theta_1}.
\end{aligned}
$$

整理後得到

$$
\mathbf C_{nm}(q;\phi)
=
e^{iq\phi}
\left[
\hat u\int_0^{2\pi} d\theta_1\,\cos^{n+1}\theta_1\,\sin^m\theta_1\,e^{iq\theta_1}
+
\hat v\int_0^{2\pi} d\theta_1\,\cos^n\theta_1\,\sin^{m+1}\theta_1\,e^{iq\theta_1}
\right].
$$

如果仍然使用純量積分

$$
C(n,m,q)=\pi\int_0^{2\pi}\cos^n\theta\,\sin^m\theta\,e^{iq\theta}d\theta,
$$

則上式可以簡寫為

$$
\mathbf C_{nm}(q;\phi)
=
\frac{e^{iq\phi}}{\pi}
\Bigl[\hat u\,C(n+1,m,q)+\hat v\,C(n,m+1,q)\Bigr].
$$

這裡可以清楚看到：在 $\hat u,\hat v$ 基底下，向量結構是自然保留下來的，不需要先退回固定的 $x,y$ 分量。

## 6. 修正後的局域形式

定義徑向與角向積分合併後的向量係數

$$
\mathbf K_{nmn_1n_2}^{(\pm)}(\phi)
:=
\int_0^\infty dr\;
r^{n+m+1}U'(r)\,
\bigl(B_s(n_1,n_2,r)\pm B_a(n_1,n_2,r)\bigr)\,
\mathbf C_{nm}(n_1;\phi).
$$

則 interaction term 可整理為

$$
\boxed{
\mathbf I[\rho]
=
\frac{\pi}{2}
\sum_{n,m,n_1,n_2}
\left[
\mathbf K_{nmn_1n_2}^{(+)}(\phi)\,D_{nm}^{(n_2)}(\mathbf r,t;\phi)\,e^{-i(n_1-n_2)\phi}
+
\mathbf K_{nmn_1n_2}^{(-)}(\phi)\,D_{nm}^{(-n_2)}(\mathbf r,t;\phi)\,e^{-i(n_1+n_2)\phi}
+
\text{c.c.}
\right]
}
$$

其中 `c.c.` 表示前面各項的 complex conjugate，因此整體 $\mathbf I$ 仍為實向量。

這個 boxed 式就是在 $\hat u,\hat v$ 基底下整理後的局域表示。

## 7. 這對 `Results.md` 代表什麼

`Results.md` 目前寫的

$$
\sum_{n,m,n_1,n_2} D_{nm}X_{n_2}Y_{C,A}\sin(n_2\phi+\psi_{n_2}+\eta_{C,A})
$$

在一般情況下 **不正確**。主要有三個結構性問題：

1. 最後留下來的 harmonic 一般是
   $e^{-i(n_1-n_2)\phi}$ 與 $e^{-i(n_1+n_2)\phi}$，
   因此結果同時依賴 $n_1$ 與 $n_2$，不是只依賴 $n_2$。

2. 乘在導數前面的係數是向量值。
   在目前這個寫法下，它們自然分解在 $\hat u,\hat v$ 基底上，而不是單一純量。

3. 導數是先作用在 $\rho_{n_2}$ 上，之後才能再抽出振幅與相位。
   也就是說，自然出現的物件其實是

   $$
   D_{nm}^{(n_2)}(\mathbf r,t;\phi)
   =
   \frac{1}{n!\,m!}\partial_u^n\partial_v^m\rho_{n_2}(\mathbf r,t),
   $$

   而不是單純的 $\rho_{n_2}$。
   如果要改寫成極座標形式，應該寫成

   $$
   D_{nm}^{(n_2)}(\mathbf r,t;\phi)
   =
   \left|D_{nm}^{(n_2)}(\mathbf r,t;\phi)\right|e^{i\chi_{nm,n_2}},
   $$

   因此相位應該是 $\chi_{nm,n_2}$，而不會一般性地等於 $\arg(\rho_{n_2})$。

## 8. 什麼情況下可以寫成正弦或餘弦形式

如果先固定某一個分量，例如 $\hat u$ 方向上的投影，並定義

$$
K_{u,+}=|K_{u,+}|e^{i\delta_{u,+}},
\qquad
D_{nm}^{(n_2)}(\mathbf r,t;\phi)
=
\left|D_{nm}^{(n_2)}(\mathbf r,t;\phi)\right|e^{i\chi_{nm,n_2}},
$$

則其中一項確實可以寫成

$$
2|K_{u,+}|\left|D_{nm}^{(n_2)}(\mathbf r,t;\phi)\right|
\cos\bigl((n_1-n_2)\phi-\delta_{u,+}-\chi_{nm,n_2}\bigr),
$$

另一支 $(n_1+n_2)$ 分支也可以做同樣處理。

所以，三角函數的振幅-相位表示並不是不能寫，而是必須滿足以下條件：

- harmonic 應該是 $(n_1\pm n_2)\phi$，不是只有 $n_2\phi$；
- 相位來自微分後的 Fourier 模態；
- 式子必須逐分量處理，或直接保留向量形式。

## 9. 總結

`Results.md` 的整體策略其實是對的：

- 先對 $g$ 在相對角度上做 Fourier 展開；
- 再對平移後的密度做 Taylor 展開；
- 再對 $\rho$ 的 $\phi'$ 依賴做 Fourier 展開；
- 最後顯式做角度積分。

但 `Results.md` 最後壓縮成單一正弦形式時，遺失了必要的結構資訊。
修正後、可直接檢查的結果就是第 6 節的 boxed 公式。
