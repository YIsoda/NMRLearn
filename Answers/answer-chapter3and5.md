---
title: 'Chapter3, 5の演習（Hartmann-Hann条件の導出）の解答例'
author: '磯田洋介'
indent: true
secnumdepth: 3
documentclass: ltjsarticle
header-includes:
  - \usepackage{braket}
  - \ltjsetparameter{jacharrange={-2,-3}}
  - \setmainfont[Ligatures=TeX]{TeX Gyre Pagella}
  - \setmathfont{TeX Gyre Pagella Math}
  - \usepackage{cancel}
microtypeoptions: false
---
## 実際に出題された演習問題を解いてみる

ここでは，ゼミの演習で出題された以下の問題を解いてみよう。

> 1. Cross Polarization
>
>    静磁場の中に異種核スピンI，Sがある場合を考える。回転座標系でZeeman相互作用$ω_{0I}I_z + ω_{0S}S_z$は見えなくなり，“truncate”された双極子相互作用は結合定数$d$を用いて
>    
>    $$H_\mathrm{d} = dI_z S_z$$
>    と表される。
>
>    また，RF照射は
>      - π/2, y pulse
>      - xパルス，強度$ω_{1I}$，$ω_{1S}$
>      - π/2, &minus;y
>
>    のように照射され，yパルスは十分短くその照射時間は$0$としてよいとする。
>
>    1.1 照射中のスピン系の時間発展はハミルトニアン
>
>    $$H = H_\mathrm{rf} + H_\mathrm{d}, H_\mathrm{rf} = ω_{1I}I_x + ω_{1S}S_x$$
>    に支配される。全体としては，トータルの時間推進演算子$U_\mathrm{total}$（y方向のRF照射に対応する時間発展演算子$U_y = e^{-i\frac{π}{2}I_y}e^{-i\frac{π}{2}S_y}$※を用いて
>
>    $$U_\mathrm{total} = U_y^{-1} e^{-itH}U_y$$
>    と表される）によって記述できる（※$(π/2)$yパルス→CP→$(π/2)$-yパルス　のようなパルスシーケンスであることを表しているが，あとでyパルスの分をCPのパルス照射に含めるように計算する）。
>
>    時間発展演算子$U_\mathrm{total}$は
>
>    $$U_\mathrm{total} = e^{itH'}, H' = H'_\mathrm{rf} + H'_\mathrm{d}$$
>    のように書き換えることができる。 **問題：$H'_\mathrm{rf}$，$H'_\mathrm{d}$を求めよ。**


>    **問題**
>    1. **$\widetilde{H}_\mathrm{d}$を計算せよ。**
>    2. **$ω_\mathrm{1I}=ω_\mathrm{1S}$の場合に$\overline{\widetilde{H}_\mathrm{d}}$を計算せよ。**
>

> 2. Cross Polarization under MAS
>
>    MASの場合，すなわちサンプルが$θ_\mathrm{m} = \cos^{-1}(1/\sqrt{3})$だけ傾いて回転している場合を考える。
>    このとき，双極子相互作用$H_\mathrm{d} = dI_z S_z$の空間部分$d$は以下のように時間依存するようになる：
>    
>    $$\begin{aligned} d(t) &= G_1\cos(γ+ω_rt) + G_2\cos(2γ+2ω_rt) \\ &= c_1\cos{ω_rt} + s_1\sin{ω_rt} + c_2\cos{2ω_rt} + s_2\sin{2ω_rt}\end{aligned}$$
>    ただし，$ω_r$はスピニングスピードである。
>    
>    **問題　$\overline{\widetilde{H'}_\mathrm{d}}$が0にならない条件を述べよ。**

**解答**

ここでは，問題に従って$\hbar$を書かない単位系で記述する。

解答に入る前に，いくつかの公式を確認しておく。

- 行列Aと正則な行列Pについて，

  $$e^{P^{-1}AP} =P^{-1}e^A P$$
  
  ∵行列の指数関数を展開すると$\sum (P^{-1}AP)^n/n!$のように表されるが，
  この$n$乗の部分は（$...P^{-1}APP^{-1}AP...$間にある$PP^{-1}$が全部消えるので）$P^{-1}A^nP$になるから。

- $[P, Q] = ikR$のような交換関係が成り立つ演算子$P, Q, R$に対して，
  
  $$e^{-iθP}Qe^{iθP} = Q\cos{kθ} + R\sin{kθ}$$

  ∵Baker-Campbell-Hausdorffの公式（たぶん行列の指数関数の定義から示せる？）に交換関係を適用すると示せるだろう。

  また，上式で$P, Q, R = I_x, I_y, I_z$とすると，演習Chapter-3-1-1で与えられている角運動量演算子の回転の公式が得られる（たぶん）

**90°傾けたバージョンのハミルトニアンの計算**　まず第一段階として，$U_\mathrm{total} = U_y^{-1} e^{-itH} U_y$を計算する。
これは，y→CP→-yのパルスを1つの時間推進演算子で表すものである。

$U_\mathrm{total}$を変形していくと，

$$
\begin{aligned}
U_\mathrm{total}&= U_y^{-1}e^{-iHt}U_y\\
  &= \exp\left(i\frac{π}{2}S_y\right)\left\{\exp\left(i\frac{π}{2}I_y\right) \exp(ω_{1I}I_x + ω_{1S}S_x + dI_z S_z)
  \exp\left(-i\frac{π}{2}I_y\right)\right\}\exp\left(-i\frac{π}{2}S_y\right)\\
  &= \exp\left(i\frac{π}{2}S_y\right)\exp\left\{\exp\left(i\frac{π}{2}I_y\right) (ω_{1I}I_x + ω_{1S}S_x + dI_z S_z)
  \exp\left(-i\frac{π}{2}I_y\right)\right\}\exp\left(-i\frac{π}{2}S_y\right)%\tag{性質1より} \\
\end{aligned}
$$

ここで，

$$
\begin{aligned}
&\exp\left(i\frac{π}{2}I_y\right) (ω_{1I}I_x + ω_{1S}S_x + dI_z S_z)\exp\left(-i\frac{π}{2}I_y\right)\\
&= ω_{1I}e^{i\frac{π}{2}I_y}I_xe^{-i\frac{π}{2}I_y} + ω_{1S}e^{i\frac{π}{2}I_y}S_x e^{-i\frac{π}{2}I_y} + d e^{i\frac{π}{2}I_y}I_z S_z e^{-i\frac{π}{2}I_y}\\
&= ω_{1I}e^{i\frac{π}{2}I_y}I_xe^{-i\frac{π}{2}I_y} + ω_{1S}S_x + d e^{i\frac{π}{2}I_y}I_z  e^{-i\frac{π}{2}I_y}S_z\\
&= ω_{1I}I_z + ω_{1S}S_x + d(-I_x)S_z
\end{aligned}
$$
となる。なぜなら，Iに関する角運動量演算子からなる演算子$e^{-i\frac{π}{2}I_y}$とスピンSに対する角運動量演算子は交換可能であるから。このように，異なるスピンを含む演算子はすり抜けてしまうと考えてよい。また，$e^{i\frac{π}{2}I_y}I_xe^{-i\frac{π}{2}I_y}$はFormulas for spin rotationで$α = -π/2$（符号に注意）としたものである。

元の式は以下のようになり，同様に計算していくと，

$$
\begin{aligned}
  &= \exp\left(i\frac{π}{2}S_y\right)\exp\left( ω_{1I}I_z + ω_{1S}S_x + d(-I_x) S_z \right)\exp\left(-i\frac{π}{2}S_y\right) \\
  &= \exp\left\{\exp\left(i\frac{π}{2}S_y\right)\left( ω_{1I}I_z + ω_{1S}S_x + d(-I_x) S_z \right)\exp\left(-i\frac{π}{2}S_y\right)\right\} \\
  &= \exp\left\{ ω_{1I}I_z + ω_{1S}S_z + d(-I_x) (-S_x) \right\} \\
  &= \exp\left( ω_{1I}I_z + ω_{1S}S_z + d I_x S_x \right) &=\exp(H'_\mathrm{rf} + H'_\mathrm{d})
\end{aligned}
$$
となるから，

$$H'_\mathrm{rf} = ω_{1I} I_z + ω_{1S}S_z, H'_\mathrm{d} = d I_x S_x$$

**RF照射をメインのハミルトニアンとしたときの相互作用表示の計算**　続いて，上記で求めたハミルトニアン$H'_\mathrm{rf} = ω_{1I} I_z + ω_{1S}S_z, H'_\mathrm{d} = d I_x S_x$を

$$H' = \underbrace{ω_{1I} I_z + ω_{1S}S_z}_{H'_0 = H'_\mathrm{rf}} + \underbrace{d I_x S_x}_{V = H'_\mathrm{d}}$$
のように分解する。ここでは文献などに従い，主となる部分を$H_0$，摂動項を$V$としてあり，今回は$H'_\mathrm{rf}$，$H'_\mathrm{d}$がそれぞれ$H_0$，$V$に対応する。
相互作用ハミルトニアン$H_\mathrm{I}$^[本研究室では$\widetilde{H}$としている]（あるいは，RFに関する回転系のハミルトニアン）は主となるハミルトニアン$H_0$による時間推進演算子$U_0(t) = e^{-iH_0t/\hbar}$を用いて$U_0^{-1}(t)VU_0(t)$で求められる。


異なる核に対する角運動量演算子は交換可能であることなどに注意して，

$$
\begin{aligned}
H_\mathrm{I} &= U_0^{-1} \left(d I_x S_x\right)U_0\\
&= e^{iω_{1S}S_zt}e^{iω_{1I} I_zt}\left(d I_x S_x\right)e^{-iω_{1I} I_zt}e^{-iω_{1S}S_zt}\\
&= d(e^{iω_{1I} I_zt} I_x e^{-iω_{1I} I_zt})(e^{iω_{1S}S_zt}S_x e^{-iω_{1S}S_zt})\\
&= d(I_x\cos{ω_{1I}t} - I_y \sin{ω_{1I}t})(S_x\cos{ω_{1S}t} - S_y\sin{ω_{1S}t})
\end{aligned}
$$
となる。MAS下では双極子相互作用の空間部分$d$が時間依存して$d(t) = c_1\cos{ω_r t} + s_1\sin{ω_r t} + c_2\cos{2ω_r t} + s_2\sin{2ω_r t}$（$c_1$～$s_2$は定数）となるので，整理すると

$$
\begin{aligned}
H_\mathrm{I} &= (c_1\cos{ω_r t} + s_1\sin{ω_r t} + c_2\cos{2ω_r t} + s_2\sin{2ω_r t})(I_x\cos{ω_{1I}t} - I_y\sin{ω_{1I}t})(S_x\cos{ω_{1S}t} - S_y\sin{ω_{1S}t})\\
&= (c_1\cos{ω_r t} + s_1\sin{ω_r t} + c_2\cos{2ω_r t} + s_2\sin{2ω_r t})×\\
& \hphantom{{}={}}(I_x S_x \cos{ω_{1I}t}\cos{ω_{1S}t}  - I_x S_y\cos{ω_{1I}t}\sin{ω_{1S}t} - I_y S_x\sin{ω_{1I}t}\cos{ω_{1S}t} + I_y S_y\sin{ω_{1I}t}\sin{ω_{1S}t})\\
&= (c_1\cos{ω_r t} + s_1\sin{ω_r t} + c_2\cos{2ω_r t} + s_2\sin{2ω_r t})×\\
& \hphantom{{}=} \{I_xS_x(\cos{(ω_{1I}+ω_{1S})t} + \cos{(ω_{1I}-ω_{1S})t})\\
& - I_xS_y(\sin{(ω_{1I}+ω_{1S})t} - \sin{(ω_{1I}+ω_{1S})t)})\\
& - I_yS_x(\sin{(ω_{1I}+ω_{1S})t} + \sin{(ω_{1I}+ω_{1S})t)})\\
& - I_yS_y(\cos{(ω_{1I}+ω_{1S})t} - \cos{(ω_{1I}-ω_{1S})t})\}×\frac{1}{2}
\end{aligned}
$$
（積→和，符号に注意）であるが，今回問題になるのは昇降演算子からなるフリップフロップ項$I_+S_- + I_-S_+ = 2(I_xS_x + I_yS_y)$である
^[昇降演算子の定義$I_± = I_x±iI_y$を用いると，$I_+S_- + I_-S_+ = (I_x+iI_y)(S_x-iS_y) + (I_x-iI_y)(S_x+iS_y) = I_xS_x + I_yS_y + I_xS_x + I_yS_y$]
から，（係数はおいといて）その項のみ抽出して^[×以下一行目と四行目の第二項をとった]

$$
\begin{aligned}
&\hphantom{{}={}} (c_1\cos{ω_r t} + s_1\sin{ω_r t} + c_2\cos{2ω_r t} + s_2\sin{2ω_r t}) × (I_xS_x + I_yS_y)\cos{(ω_{1I}-ω_{1S})t}\\
&= \frac{1}{2}(I_xS_x + I_yS_y)×\{\\
& c_1(\cos{(ω_r+(ω_{1I}-ω_{1S})t)}+\cos{(ω_r-(ω_{1I}-ω_{1S})t)}) \\
& s_1(\sin{(ω_r+(ω_{1I}-ω_{1S})t)}+\sin{(ω_r-(ω_{1I}-ω_{1S})t)}) \\
& c_2(\cos{(2ω_r+(ω_{1I}-ω_{1S})t)}+\cos{(2ω_r-(ω_{1I}-ω_{1S})t)}) \\
& s_2(\sin{(2ω_r+(ω_{1I}-ω_{1S})t)}+\sin{(2ω_r-(ω_{1I}-ω_{1S})t)}) \\
\}
\end{aligned}
$$
これを時間で積分すると$ω_{1I} = ω{1S} ± ω_r t, ± ω_r t$の時のみ$\cos{0}$の項が生じ，従って時間平均して0にならずに残るので，磁化の移動が起こる。よって，MAS速度（角周波数）$ω_r$のMAS下におけるHartmann-Hann条件は

$$ω_{1I} = ω_{1S} ± ω_r t, ± 2ω_r t$$
