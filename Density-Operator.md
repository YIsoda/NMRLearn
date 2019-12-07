---
title: 'いまさら納得する　密度演算子・磁化の時間発展'
author: '磯田洋介'
indent: true
secnumdepth: 3
documentclass: ltjsarticle
header-includes:
	- \usepackage{braket}
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

## 密度演算子の直積展開？

## 相互作用表示　～Schrödinger描像とHeisenberg描像と関連付けて～

- Schrodinger描像
- Heisenberg描像
- 相互作用描像（Interaction picture）

それぞれ添え字${}_\mathrm{S}$，${}_\mathrm{H}$，${}_\mathrm{I}$を用いて区別する場合がある。
