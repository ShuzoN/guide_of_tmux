## a_guide_of_tmux

@ShuzoN

---

## はじめに

---

#### こんな人に聞いて欲しい

 * あんまりターミナルを使ったことがない
 * ごりごりターミナル使うけどカスタマイズ面倒
 * 重い処理中にターミナルが落ちて萎えたことがある
 * iTermでターミナル複数起動してる
 
---

#### はじめに

tmux (てぃーまっくす)とは, 多重端末を  
提供するツールのこと.

一つのターミナルで  
複数個のターミナルを起動できる. 

---

#### はじめに

[本家](https://github.com/tmux/tmux/wiki) より

```
tmux is a terminal multiplexer.   
It lets you switch easily between   
several programs in one terminal,   
detach them (they keep running in the background)   
and reattach them to a different terminal. 
```

---

### tmuxの雰囲気をつかむ

---

### あなたのターミナルこんなことになってませんか??

---
#### うわっ, 私のターミナル...多すぎ...


![image](https://user-images.githubusercontent.com/5877377/27993187-522a0218-64df-11e7-8e8c-8dc76e53ecbf.png)


---
#### iTerm でターミナル複数起動
![image](https://user-images.githubusercontent.com/5877377/27993244-34c03ee8-64e1-11e7-9a40-db3c98053896.png)


---

tmuxはこんなの
![image](https://user-images.githubusercontent.com/5877377/27993212-466591b2-64e0-11e7-9075-3abfd355a32f.png)

---


#### tmuxを使うと嬉しいこと

 * 1つの端末で複数の端末を起動可能
   - 複数の端末を立ち上げずに、tmux上の擬似端末を切り替えてオペレーション可能
  
 * 起動した端末を画面分割して使用可能
   - 他のファイルを参照したりログ出力を参照しながらオペレーション可能

---

#### tmuxを使うと嬉しいこと part 2
 
 * 起動した端末のデタッチ(切り離し)/アタッチ(接続)が可能
   - クライアント・サーバで動作する
   - サーバがターミナルの情報を保持(セッション)
   - クライアントはサーバが持つセッションに接続する
   - サーバとの接続が切れてもセッションが残っていれば再接続可能
   - 異なる環境から同じtmuxセッションへ接続可能

参考 : http://kanjuku-tomato.blogspot.jp/2014/02/tmux.html



---

### tmuxを使ってみる

---

#### インストール

tmux 2.5を使う

mac 

```sh
$ brew install tmux
```

linux

```sh
 # tar.gzのリンクあげるから頑張ってほしい
 https://github.com/tmux/tmux/releases/download/2.5/tmux-2.5.tar.gz
```
---
