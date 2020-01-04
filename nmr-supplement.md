---
title: |
  | NMRの時間発展の理解を助ける基礎理論のメモ
  | ～いまさら初歩から納得する　磁化の時間発展～ 
author: 'Yosuke Isoda'
indent: true
secnumdepth: 3
documentclass: ltjsarticle
header-includes:
  - \hypersetup{pdftitle=NMRの時間発展の理解を助ける基礎理論のメモ～いまさら初歩から納得する　磁化の時間発展～}
  - \usepackage{braket}
  - \ltjsetparameter{jacharrange={-2,-3}}
  - \setmainfont[Ligatures=TeX]{TeX Gyre Pagella}
  - \setmathfont{TeX Gyre Pagella Math}
  - \usepackage{cancel}
microtypeoptions: false
---

<!-- markdownlint-disable-file single-title -->

# はじめに

このドキュメントでは，本研究室の演習で出てくるようなNMRの磁化のふるまいを理解するのに必要な量子力学のうち，私が必要だと思った部分で足りていなかった・足りていない部分（密度演算子／密度行列などをふくむ）について解説します。

分かりやすさを優先し，あまり数学的な厳密さは求めませんが，ある程度なぜあのように計算してよいのかが理解できるくらいには詳しく説明します。
また，私のように数学がそんなに得意でない人でもつまづかないよう，計算例などの過程を（冗長さとのバランスを取りつつもできるだけ）詳しく記述します。

## 前提知識など
<!-- Todo: 前提知識，知っておいたほうが良いこと -->
本ドキュメントでは，量子力学の基礎やbra-ket記法などを前提とします。

## 参考資料

現時点では，以下の書籍を参考にしました。特に，磁気共鳴-NMRを読んでいてわからなかったところを補足的に勉強するのに役立てたらいいと思っています。

- [磁気共鳴-NMR（竹腰，サイエンス社，2011）](https://www.saiensu.co.jp/search/?isbn=978-4-7819-1295-0&y=2011)
- [入門　量子ダイナミクス --時間依存の量子力学を中心に--（上）（David J. Tannor，山下晃一ほか訳，化学同人，2011）](https://www.kagakudojin.co.jp/book/b92546.html)
  
  特に，
  - 第5章　Wigner表示と密度演算子
  - 第9章　時間依存Schrödinger方程式の近似解

また，以下のWebサイトも大いに参考にしました。

- 物理とか（<https://whyitsso.net/>）
  - 量子力学のページ（<https://whyitsso.net/physics/quantum_mechanics/index.html>）
- EMANの物理学（<https://eman-physics.net>）
  - 量子力学（<https://eman-physics.net/quantum/contents.html>）

## 単位系など

本稿では原則SI単位系を使います（つまり，$\hbar$などを省きません）。
なお，演習問題で問題が$\hbar$を書かない単位系で記述されている場合などに限りその単位系を利用しました。

# ［作成中］1スピンのSchrödinger方程式と解

# ［作成中］密度演算子［密度行列］の導入とLeuville-von Neumann方程式

本節では，Schrödinger方程式を前提にして，たくさんの核があるとき（混合状態）に役立つ「密度演算子」の考え方を導入する。

密度行列$\displaystyle \hat{ρ} = \sum_i p_i \ket{ψ}\bra{ψ}$

Leuville-von Neumann方程式$\displaystyle i\hbar \frac{∂\hat{ρ}}{∂t} = [\hat{H}, \hat{ρ}] = \hat{H}\hat{ρ} - \hat{ρ}\hat{H}$

Schrodinger方程式

### Leuville von Neumann方程式の導出

$$i\hbar\frac{∂ψ}{∂t} = \hat{H}ψ$$
（形式的に解くと$ψ(t) = e^{-i\hat{H}t/\hbar} ψ(0)$）と密度演算子の定義からLeuville-von Neumann方程式を導こう。

純粋状態（混合状態ではなくある状態ベクトルで表される）について考える。この密度演算子

$$\hat{ρ} = \ket{ψ}\bra{ψ}$$
の両辺を時間微分すると，

$$\frac{∂\hat{ρ}}{∂t} = \left(\frac{∂}{∂t}\ket{ψ_i}\right)\bra{ψ_i} + \ket{ψ_i}\left(\frac{∂}{∂t}\bra{ψ_i}\right)$$

Schrodingere方程式より$\frac{∂\ket{ψ}}{∂t} = \frac{1}{i\hbar}\hat{H}\ket{ψ}$およびエルミート共役をとって$\frac{∂\bra{ψ}}{∂t} = -\frac{1}{i\hbar}\bra{ψ}\hat{H}$（$\hat{H}$はエルミート演算子）を代入すると，

$$
\begin{aligned}
&= \left(\frac{1}{i\hbar}\hat{H}\ket{ψ}\right)\bra{ψ} - \ket{ψ}\left(\frac{1}{i\hbar}\bra{ψ}\hat{H}\right)\\
&= \frac{1}{i\hbar}\left(\hat{H}\hat{ρ} - \hat{ρ}\hat{H}\right)\\
&= \frac{1}{i\hbar} \left[\hat{H},\hat{ρ} \right]
\end{aligned}
$$


さて，混合状態についてはどうだろうか。混合状態も含めた場合について密度演算子は
$\displaystyle \hat{ρ} = \sum_i p_i \ket{ψ}\bra{ψ}$
である。
**たくさんの粒子が集まっている系について，その粒子の数が増減することは考えず，個々の粒子がそれぞれ時間発展することから$p_i$は時間に依存しない定数である**ので$dp_i/dt = 0$であることに留意すると（ここが自分的にはしっくりこなかった），
上記と同様にLeuville von Neumann方程式が導出できる。

参考 https://ocw.kyoto-u.ac.jp/ja/graduate-school-of-science-jp/course-chemical-statics/pdf/lect10.pdf

### Leuville von Neumann方程式を形式的に解く

ハミルトニアンが時間に依存しない場合，Leuville von Neumann方程式は形式的に解け，解は$\hat{ρ}(t) = e^{-i\hat{H}t/\hbar} ρ(0) e^{i\hat{H}t/\hbar} = U(t)ρ(0) U(t)^{-1}$となる。ここで，$U$は時間発展演算子などと呼ばれる。

実際，上式をLeuville von Neumann方程式の左辺に代入すると，

$$
\begin{aligned}
i\hbar \frac{d}{dt}\left( e^{-i\hat{H}t/\hbar} ρ(0) e^{i\hat{H}t/\hbar} \right) &= i\hbar\left(  \frac{d}{dt}(e^{-i\hat{H}t/\hbar} )ρ(0) e^{i\hat{H}t/\hbar} + e^{-i\hat{H}t/\hbar} ρ(0)  \frac{d}{dt}(e^{i\hat{H}t/\hbar}) \right) \\
&= i\hbar\left( \left(-\frac{i\hat{H}}{\hbar}\right)e^{-i\hat{H}t/\hbar} ρ(0) e^{i\hat{H}t/\hbar} +e^{-i\hat{H}t/\hbar} ρ(0) \frac{i\hat{H}}{\hbar}e^{i\hat{H}t/\hbar} \right)\\
&= -i\hbar\left( \frac{i\hat{H}}{\hbar}e^{-i\hat{H}t/\hbar} ρ(0) e^{i\hat{H}t/\hbar} -e^{-i\hat{H}t/\hbar} ρ(0) e^{i\hat{H}t/\hbar}\frac{i\hat{H}}{\hbar} \right)\\
&= \hat{H}ρ - ρ\hat{H} = [\hat{H}, ρ]
\end{aligned}
$$
（ここではハミルトニアンは時間に依存しないとしているので指数の肩でも時間微分に対して定数として計算してよく，また$H$とその指数関数は交換できる。が，密度演算子とハミルトニアン，およびそれらの指数関数は交換可能ではないのでかってに入れ替えたりはしない！）
となって，これが解になっていることが確認できる。

## 混合状態

# ［作成中］密度演算子の直積展開

本節では磁化の状態が$I_z$などと表すことができる背景を探っていく。

一般に，任意のエルミート演算子は，$\mathrm{Tr}[\hat{F_i}, \hat{F_j}] = cδ_{ij}$のように規格直交化された演算子の完全系$\{\hat{F_i}\}$で展開できる
（Wikipedia情報： [理論｜直積演算子 - Wikipedia](https://ja.wikipedia.org/wiki/%E7%9B%B4%E7%A9%8D%E6%BC%94%E7%AE%97%E5%AD%90#%E7%90%86%E8%AB%96)）

密度演算子も同様に展開できるので，基底演算子として，各スピン角運動量演算子の直積を採用する。
（いくつかの近似が入る）

今，1スピン系について

$$E/2 = \frac{1}{2}\begin{pmatrix}1&0\\0&1\end{pmatrix},I_x, I_y, I_z$$
を基底にとると，例えばある状態が密度演算子で$ρ(t=0) \propto I_z$などと表現されるだろう。前節で確認したように，この期待値は<!-- Todo:詳しく -->

$$
\left\langle \hat{I_z}\right\rangle =　\sum_i \Braket{ψ_i|\hat{I_z}ρ|ψ_i} \propto \sum_i \Braket{ψ_i|\hat{I_z}I_z|ψ_i}
$$
（Z成分角運動量の場合）と表された（一応$ψ$に挟まれてる部分の左の$\hat{I_z}$が今期待値を求めたい演算子$A$，右の$I_z$が系の状態を表す密度演算子のつもり）。
$\hat{I}_z\hat{I_z} = \begin{pmatrix}1&0\\0&-1\end{pmatrix}\begin{pmatrix}1&0\\0&-1\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}$であるから値が出る。一方，この状態の$\hat{I_x}$に対する期待値を計算すると0になる。

ここでは，角運動量演算子では直交するものを基底に選んでいることから，$\sum_i \Braket{ψ_i|\hat{A}ρ|ψ_i}, \hat{A} = \hat{I}_x, \hat{I}_y, \hat{I}_z$の挟まれている$\hat{A}ρ$の部分は$\hat{A}$と$ρ$が同じ方向の角運動量演算子の場合にのみ0でない演算子となり，したがって全体として0でない期待値をもつ可能性がある。

# 相互作用表示　～Schrödinger描像とHeisenberg描像と関連付けて～

本節ではよく出てくる“回転系”の理解のために，

- Schrodinger描像
- Heisenberg描像
- 相互作用描像（Interaction picture）

（それぞれ添え字${}_\mathrm{S}$，${}_\mathrm{H}$，${}_\mathrm{I}$を用いて区別する場合がある）
について考え，また平均ハミルトニアンを考える準備とする。

本項では主に「入門量子ダイナミクス」の流れに従って相互作用描像を記述する。

## 時間依存Schrödinger方程式とHeisenberg方程式，近似のない相互作用描像による時間発展

- Schrodinger描像
  
  演算子は時間変化せず，状態ベクトルが時間変化するというもの。

  $$i\hbar \frac{∂Ψ_\mathrm{S}(t)}{∂t} = \hat{H}_\mathrm{S}Ψ(t)_\mathrm{S}$$

  $\hat{H}$が時間に依存しない場合，（$\hat{H}$はただの定数として計算しても答えと合致）

  $$Ψ(t)_\mathrm{S} = e^{-\frac{i}{\hbar}\hat{H}_\mathrm{S}t}Ψ_\mathrm{S}(0)$$
  である。$e^{-\frac{i}{\hbar}\hat{H}_\mathrm{S}t} = U(t)$と置き，$U$を時間発展演算子と呼ぶ。

  また，ある演算子$A$の期待値（期待値は時間の関数である）は

  $$
  \begin{aligned}
  \langle A\rangle &= \Braket{Ψ(t)|A|Ψ(t)} \\
  &=\Braket{Ψ(t)|A|Ψ(t)}\\
  &=\Braket{U(t)Ψ(0)|A|U(t)Ψ(0)}
  \end{aligned}
  $$
  と表される。

- Heisenberg描像

  - Heisenberg描像での波動関数$Ψ_\mathrm{H}(t)$を$Ψ_\mathrm{H}(t) = e^{\frac{i}{\hbar}Ht}Ψ_\mathrm{S}(t)$と定義すると，
    
    $$Ψ_\mathrm{H}(t) =  e^{\frac{i}{\hbar}Ht} \left( e^{-\frac{i}{\hbar}Ht}Ψ_\mathrm{S}(0)\right) = Ψ_\mathrm{S}(0)$$
    で，状態ベクトルは時間変化しない。
  - あるいは，

    $$\langle A\rangle = \Braket{U(t)Ψ_\mathrm{S}(0)|A|U(t)Ψ_\mathrm{S}(0)} = \Braket{Ψ_\mathrm{S}(0)|\left(U^{-1}(t)AU(t)\right)|Ψ_\mathrm{S}(0)}$$
    で$\left(U^{-1}(t)AU(t)\right) = A_\mathrm{H}$，$Ψ_\mathrm{S}(0) = Ψ_\mathrm{H}(0)$とおくと

    $$\Braket{Ψ_\mathrm{H}(0)|A_\mathrm{H}(t)|Ψ_\mathrm{H}(0)}$$
    となり，期待値の変化が演算子が時間変化に依存するように書ける。

  このように，Schrödinger描像とことなり，状態ベクトルは時間変化せず演算子が時間変化するように表現できるが，期待値はSchrödinger描像と一致する。

- 相互作用描像（Interaction image）
  
  全ハミルトニアン$H$を，$H_0$と$H_1$にわけることを考える（あとで述べるように時間依存のハミルトニアンである場合には時間に依存する部分を$H_1$に含め，$H_0$を時間に依存しないようにとるとよい）。

  $$\hat{H} = \hat{H}_0 + \hat{H}_1$$
  相互作用描像の波動関数$Ψ_\mathrm{I}(t)$を，Schrödinger描像の波動関数$Ψ_\mathrm{S}(t)$を用いて

  $$Ψ_\mathrm{I}(t) = e^{\frac{i}{\hbar}\hat{H}_0t}Ψ_\mathrm{S}(t) = e^{\frac{i}{\hbar}\hat{H}_0t}e^{-\frac{i}{\hbar}\hat{H}t}Ψ_\mathrm{S}(0)$$
  と定義する。もし「多くの部分」の時間発展が$H_0$によっているとすると，$e^{\frac{i}{\hbar}\hat{H}_0t}$の時間発展と$e^{-\frac{i}{\hbar}\hat{H}t}$の時間発展が打ち消しあい，$Ψ_\mathrm{I}$はほとんど時間発展しない。

  $Ψ_\mathrm{S} = e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{S}(t)$であるから，これを時間依存のSchrödinger方程式に代入すれば相互作用描像の波動関数の運動方程式が得られる。

  $$
  \begin{aligned}
  i\hbar\frac{∂}{∂t}\left(  e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t) \right) &= \hat{H} \left(e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t)\right)\\
  i\hbar e^{-\frac{i}{\hbar}\hat{H}_0 t} \left( -\frac{i}{\hbar}\hat{H}_0 Ψ_\mathrm{I} + \frac{∂Ψ_\mathrm{I}(t)}{∂t}\right) &= (\hat{H}_0 + \hat{H}_1)\left(e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t)\right)\\
  \cancel{e^{-\frac{i}{\hbar}\hat{H}_0 t}\hat{H}_0 Ψ_\mathrm{I} }+ i\hbar e^{-\frac{i}{\hbar}\hat{H}_0 t} \frac{∂Ψ_\mathrm{I}(t)}{∂t} &= \hat{H}_0 e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t) + \hat{H}_1 e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t) \\
  &= \cancel{ e^{-\frac{i}{\hbar}\hat{H}_0 t} \hat{H}_0 Ψ_\mathrm{I}(t) } + \hat{H}_1 e^{-\frac{i}{\hbar}\hat{H}_0 t} Ψ_\mathrm{I}(t)
  \end{aligned}
  $$
  （$H_0$と$H_1$のような異なる演算子およびその指数関数は一般に交換しないことに注意。）残った部分に左から$e^{+\frac{i}{\hbar}\hat{H}_0t}$をかけて，

  $$
  \begin{aligned}
  i\hbar \frac{∂Ψ_\mathrm{I}(t)}{∂t} &= e^{\frac{i}{\hbar}\hat{H}_0 t} \hat{H}_1 e^{-\frac{i}{\hbar}\hat{H}_0 t}Ψ_\mathrm{I}(t)\\
  &=\hat{H}_\mathrm{I}Ψ_\mathrm{I}(t)
  \end{aligned}
  $$
  ここで，相互作用描像のハミルトニアンを$\hat{H}_\mathrm{I}$とした。

以上，各描像の演算子や方程式を確認した。相互作用描像は次項で述べるように時間依存接道論の文脈で重要になる。

## 相互作用描像の例：Zeeman相互作用とRF照射のみを考えるケース

時間依存摂動論に入る前に，摂動展開による近似なしでいい場合を考える。ただし，「高温近似・弱く結合したスピン系であること・緩和は無視できる」ことを仮定し（参考：Wikipediaの直積演算子法のページ），したがって系の初期状態は密度演算子$ρ \propto I_z$と表されるとする。
Z方向の静磁場$\boldsymbol{B} = (0, 0, B)$とRF照射$\boldsymbol{B}_1 = (0, 2B_1 \cos{ω_0 t}, 0)$のみが相互作用として考えるとき，（もともとの/Schrodinger/全）ハミルトニアンは

$$
\begin{aligned}
H &= -γ\hbar\boldsymbol{I}⋅\boldsymbol{B} + ( -2γ\hbar B_1I_y \cos ω_0t)\\
&= \hbar ω_0 I_z + 2\hbar ω_1 I_y \cos{ω_0 t}
\end{aligned}
$$
と表せる^[磁場$\boldsymbol{B}$についてハミルトニアンは$-γ\hbar\boldsymbol{I}\cdot\boldsymbol{B}$]（ただし$ω_0 = -γB_0$，$ω_1 = -γB_1$，$γ$は磁気回転比）。

ここで，ハミルトニアンを

$$
\begin{aligned}
H &= \underbrace{\hbar ω_0 I_z}_{H_0} + \underbrace{2\hbar ω_1 I_y \cos{ω_0 t}}_V\\
&= H_0 + V(t)
\end{aligned}
$$
のように時間に依存しない部分と時間に依存する部分の二つの項に分ける。後者は摂動項と呼ばれるが，今回の場合摂動展開による近似は行わない。

さて，相互作用ハミルトニアンは，非摂動ハミルトニアン$H_0$を用いた時間発展演算子$U_0 = e^{-iH_0 t/\hbar}$を用いて，摂動項を

$$
H_\mathrm{I} = U_0^{-1} V U_0
$$
のように変換すればよいのであった。これは，

$$
\begin{aligned}
H_\mathrm{I} &= U_0^{-1} V U_0\\
&= e^{iH_0t/\hbar}2\hbar ω_1I_y\cos{ω_0 t}e^{-iH_0t/\hbar}\\
&= 2\hbar ω_1\cos{ω_0 t} \left( e^{iω_0 I_z t} I_y e^{-iω_0 I_z t} \right)\\
&= 2\hbar ω_1\cos{ω_0 t} \left( I_y\cos{ω_0 t} + I_x\sin{ω_0 t} \right)\\
&= 2\hbar ω_1\left( I_y \cos^2{ω_0 t} + I_x\cos{ω_0 t}\sin{ω_0 t} \right)\\
&= \hbar ω_1 \left( I_y (1 + \cos{2ω_0 t}) + I_x \sin{2ω_0 t}\right)
\end{aligned}
$$
のように変形でき，このうちラーモア周波数の2倍で振動している成分は“truncate”できて無視されるので，結局相互作用ハミルトニアンは

$$H_\mathrm{I} = \hbar ω_1 I_y$$
となる。上記のハミルトニアンは相互作用描像のハミルトニアンであると同時に，RF照射の周波数で回転する回転系^[ここではオフセットを考えていないのでこれは静磁場のラーモア周波数と一致する]のハミルトニアンであるとも言える。

これは時間に依存せず，このハミルトニアンに関するLiuville von Neumann方程式

$$i\hbar\frac{dρ}{dt} = \left[H_\mathrm{I}, ρ\right]$$
は厳密に解け，また初期状態でZ磁化が生じている（$ρ(t=0)∝I_z$）ことから，相互作用ハミルトニアン$H_\mathrm{I}$の時間発展演算子$U_\mathrm{I}(t)$を用いて

$$
\begin{aligned}
ρ(t) &= U_\mathrm{I}(t)ρ(0)U_\mathrm{I}^{-1}(t) = e^{-i ω_1 I_y t}I_z e^{i ω_1 I_y t}\\
&= I_z \cos{ω_1 t} + I_x \sin{ω_1 t}
\end{aligned}
$$
となる。これは，yパルスによって磁化がy軸回りに回転することを意味し，巨視的な磁化を回転座標系にのせて考えたときと一致する。

## 相互作用表示と時間依存摂動論

時間非依存のハミルトニアン$H$に対して，Schrödinger方程式

$$i\hbar\frac{∂}{∂t}Ψ(x,t) = HΨ(x,t)$$
は，

$$Ψ(x,t) = e^{-iHt/\hbar}Ψ(x, 0)$$
と書き換えられた。ハミルトニアンが時間に依存する場合

#### **メモ**（あとでまとめる）

<https://whyitsso.net/physics/quantum_mechanics/perturbation5.html>より

Magnus展開

$$U_\mathrm{I}(t) = e^{-i\left[ Ω^{(1)}(t) + Ω^{(2)}(t) + \cdots \right]}$$

ただし，

$$Ω^{(0)}(t) = 0$$

$$Ω^{(1)}(t) = \int_0^t dt_1 H_\mathrm{I}(t_1)$$

$$Ω^{(2)}(t) = \frac{i}{2}\int_0^t dt_1 \int_0^{t_1} dt_2 \left[H_\mathrm{I}(t_1), H_\mathrm{I}(t_2)\right]$$

一次の項までとると，

$$U_\mathrm{I} ≃ \exp{\left\{-i\int_0^t dt' H_\mathrm{I}(t')\right\}}$$

ここで，相互作用ハミルトニアンが時間依存しない場合を考えると$\displaystyle \int_0^t dt'H_\mathrm{I}(t') = H_\mathrm{I}t$であり，$U_\mathrm{I} = e^{-iHt/\hbar}$となり，前のほうで考えた時間推進演算子と一致する。

これによって，相互作用表示に置ける波動関数の時間発展は$ψ(t) = U_\mathrm{I}(t)ψ(0)$となる（または密度演算子の時間発展は$ρ_\mathrm{I}(t) = U_\mathrm{I}(t)ρ(0)U(t)_\mathrm{I}^{-1}$となる）。

## 実際に出題された演習問題を解いてみる

ここでは，ゼミの演習で出題された以下の問題を解いてみよう。

メモ：RFの方向をzになるように一旦回転させてるのはFlip-Flopの説明のため？

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

**解答例**

ここでは，問題に従って$\hbar$を書かない単位系で記述する。

解答に入る前に，いくつかの公式を確認しておく。

- 行列Aと正則な行列Pについて，

  $$e^{P^{-1}AP} =P^{-1}e^A P$$
  
  ∵行列の指数関数を展開すると$\sum (P^{-1}AP)^n/n!$のように表されるが，
  この$n$乗の部分は（$...P^{-1}APP^{-1}AP...$間にある$PP^{-1}$が全部消えるので）$P^{-1}A^nP$になるから。

- $[P, Q] = ikR$のような交換関係が成り立つ演算子$P, Q, R$に対して，
  
  $$e^{-iθP}Qe^{iθP} = Q\cos{kθ} + R\sin{kθ}$$<--ほんまか？ -->

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



以下，問題の形式に従って$\hbar$を書かない単位で表現する。異なる核に対する角運動量演算子は交換可能であることなどに注意して，

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
となる（解答終わり）。
