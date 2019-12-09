---
title: 'いまさら納得する　密度演算子・磁化の時間発展'
author: '磯田洋介'
indent: true
secnumdepth: 3
documentclass: ltjsarticle
header-includes:
  - \usepackage{braket}
  - \ltjsetparameter{jacharrange={-2,-3}}
  - \setmainfont[Ligatures=TeX]{TeX Gyre Pagella}
  - \setmathfont{TeX Gyre Pagella Math}
microtypeoptions: false
---

# About Density operator

このドキュメントでは，NMRの磁化のふるまいを理解するのに必要な量子力学，なかでも密度演算子／密度行列について解説します。

分かりやすさを優先し，あまり数学的な厳密さは求めませんが，ある程度なぜあのように計算してよいのかが理解できるくらいには詳しく説明します。
また，（私のように数学がそんなに得意でない人でもつまづかないように）計算例などの過程を冗長さとのバランスを取りつつできるだけ詳しく記述します。

本ドキュメントでは，

- 量子力学の基礎，なかでもbra-ket記法

- 
- 

を前提とします。

References

- 入門　量子ダイナミクス --時間依存の量子力学を中心に--（上）
  - 第9章

## 1スピンのSchrödinger方程式と解

$\left|1\right\rangle$

## 密度演算子［密度行列］の導入とLeuville-von Neumann方程式

密度行列$\displaystyle \hat{ρ} = \sum_i p_i \ket{ψ}\bra{ψ}$

Leuville-von Neumann方程式$\displaystyle i\hbar \frac{∂\hat{ρ}}{∂t} = [\hat{H}, \hat{ρ}] = \hat{H}\hat{ρ} - \hat{ρ}\hat{H}$

Schrodingere方程式

#### Leuville von Neumann方程式の導出

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

参考 https://ocw.kyoto-u.ac.jp/ja/graduate-school-of-science-jp/course-chemical-statics/pdf/lect10.pdf


### 混合状態

## 密度演算子の直積展開

（$\hbar$が入るので多少面倒だがSI系？を採用）

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

## 相互作用表示　～Schrödinger描像とHeisenberg描像と関連付けて～

- Schrodinger描像
- Heisenberg描像
- 相互作用描像（Interaction picture）

それぞれ添え字${}_\mathrm{S}$，${}_\mathrm{H}$，${}_\mathrm{I}$を用いて区別する場合がある。

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
