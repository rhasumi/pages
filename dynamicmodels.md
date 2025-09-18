---
layout: default
title: 『動学マクロ経済学へのいざない』
permalink: /dynamicmodels/
nav_order: 2
---

# 『動学マクロ経済学へのいざない』サポートページ
[蓮見 亮（著）『動学マクロ経済学へのいざない』、日本評論社、2020年](https://www.nippyo.co.jp/shop/book/8267.html) [Amazon](https://www.amazon.co.jp/dp/453555949X)

2013年ごろより掲載していた「講義ノート：動学マクロ経済学入門」を一部加筆修正のうえ2020年3月に日本評論社から単行本として刊行しました（[Kindle版](https://www.amazon.co.jp/dp/B086VXVYYT/)あり）。
* [正誤表](http://www.rhasumi.net/data/dmacro_errata.pdf) 
* [プログラム](https://github.com/rhasumi/dynamicmodels)（GitHub）
  * プログラム言語はRファイルはR、mファイルはMatlab/Octave、modファイルはDynareです
* [Dynare の使い方について](https://github.com/rhasumi/dynamicmodels/blob/master/use_dynare.pdf)（PDF、2025年9月版）

## Rプログラムの実行方法

### Rのインストール
- [CRAN](https://cran.ism.ac.jp/)よりインストーラがダウンロードできるので、インストーラの指示に従ってインストールする
- `nleqslv`というパッケージを用いるので、インターネットにアクセス可能な状態で、Rコンソール上で
```
install.packages("nleqslv")
```
というコマンドを実行する

### Rプログラムの実行
方法は2通り
- 簡単なのは、プログラムファイルをエディタで開いて全文コピーし、Rコンソール上にペーストする
- 上記を一行コマンドで実行したければ、`setwd()` 関数で作業ディレクトリをプログラムファイルがある場所に指定した後、
```
source("programname.R")
```
というコマンドを実行する（programname.Rの部分は、実行したいプログラムに応じて変更する）

## Dynareプログラム（modファイル）の実行方法
### OctaveとDynareのインストール
- まず、[Dynareのページ](http://www.dynare.org/download)からDynareのインストーラがダウンロードできるので、インストーラの指示に従ってインストールする
- 次に、インストールしたDynareの指定するOctaveのバージョンに合わせて、[GNU Octaveのページ](https://octave.org/download.html)よりOctaveのインストーラをダウンロードし、インストーラの指示に従ってインストールする
  - MATLABがインストールされていれば、Octaveは不要

### Dynareプログラム（modファイル）の実行
詳しくは[Dynare の使い方について](https://github.com/rhasumi/dynamicmodels/blob/master/use_dynare.pdf)参照

Octave/MATLABの起動後、

1. Dynareにパスを通す（addpathコマンド）（例）
```
addpath C:\programs\dynare\6.4\matlab
```
2. modファイルのある場所を作業フォルダとして指定（cdコマンド）（例）
```
cd 'C:\Documents and Settings\USERNAME\My Documents\dynare'
```
3. dynareコマンドで実行（例）
```
dynare RBC_det
```
