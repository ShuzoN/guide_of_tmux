## guide_of_tmux

@ShuzoN

---

## はじめに

---
#### はじめに

tmux (てぃーまっくす)とは, 仮想多重端末を  
提供するツールのこと.

一つのターミナルで仮想的に  
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

#### インストール

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

### tmuxの雰囲気をつかむ

---

こんなの
![tmuxのイメージ](https://user-images.githubusercontent.com/5877377/27993105-7da30e78-64dd-11e7-8be1-decce13d88cf.jpg)

---

#### tmuxを使うと嬉しいこと

tmuxを使うことによるメリット

 * 1つの端末で複数の擬似端末を起動可能
  - 複数の端末を立ち上げずに、tmux上の擬似端末を切り替えてオペレーション可能
 * 起動した仮想端末を画面分割して使用可能
  - 他のファイルを参照したりログ出力を参照しながらオペレーション可能
 * 起動した仮想端末上でコピペが可能
  - マウスを使わず、tmux内でキーボードのみでのコピペが可能
 * 起動した仮想端末のデタッチ(切り離し)/アタッチ(接続)が可能
  - tmux実行端末とのネットワークが切れても問題なく、異なる環境から同じtmuxセッションへ接続可能

参考 : http://kanjuku-tomato.blogspot.jp/2014/02/tmux.html


---
