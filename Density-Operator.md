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

## 1スピンのSchrödinger方程式と解

$\left|1\right\rangle$

## 密度演算子［密度行列］の導入とLeuville-von Neumann方程式

密度行列$\displaystyle \hat{ρ} = \sum_i p_i \ket{ψ}\bra{ψ}$

Leuville-von Neumann方程式$\displaystyle i\hbar \frac{∂\hat{ρ}}{∂t} = [\hat{H}, \hat{ρ}] = \hat{H}\hat{ρ} - \hat{ρ}\hat{H}$

### 混合状態

## 密度演算子の直積展開

（$\hbar$が入るので多少面倒だがSI系？を採用）

一般に，任意のエルミート演算子は，$\mathrm{Tr}[\hat{F_i}, \hat{F_j}] = cδ_{ij}$のように規格直交化された演算子の完全系$\{\hat{F_i}\}$で展開できる（Wikipedia情報 [理論｜直積演算子 - Wikipedia](https://ja.wikipedia.org/wiki/%E7%9B%B4%E7%A9%8D%E6%BC%94%E7%AE%97%E5%AD%90#%E7%90%86%E8%AB%96)）

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
