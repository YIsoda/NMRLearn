# NMRの時間発展の理解を助ける補足資料

[![CircleCI](https://circleci.com/gh/YIsoda/NMRLearn/tree/master.svg?style=svg)](https://circleci.com/gh/YIsoda/NMRLearn/tree/master)

本ドキュメントは研究室で授業や演習をやっていて自分が躓いたところなどをまとめてみたものです。

## PDFファイルの利用方法

現在のところ，編集途中のPDFファイルは [GitHubプロジェクトのページ](https://github.com/YIsoda/NMRLearn/projects/1#column-7411344) に適宜リンクを貼っています。

## 自前でPDFファイルを生成する方法

PDFファイルを組版するのにLaTeXを利用しています。以下の方法を実行するにはTeX Liveをインストールしてください（以下では最新版のTeX Liveを前提とします）。

- Markdown(`.md`)ファイルからPDFファイルを生成する
  
  最新版の [Pandoc](https://pandoc.org/installing.html) をインストールし，以下のコマンドでTeXファイル，続いてPDFファイルを生成します。
  
  ```
  pandoc --standalone --to=latex+auto_identifiers+latex_macros --number-sections --output=nmr-supplement.tex nmr-supplement.md
  cluttex --engine=lualatex nmr-supplement.tex
  ```
