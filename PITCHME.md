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

### あなたのターミナルこんなことになってませんか??

---
#### うわっ, 私のターミナル...多すぎ...


![image](https://user-images.githubusercontent.com/5877377/27993187-522a0218-64df-11e7-8e8c-8dc76e53ecbf.png)


---
#### iTerm でターミナル複数起動
![image](https://user-images.githubusercontent.com/5877377/27993244-34c03ee8-64e1-11e7-9a40-db3c98053896.png)


---

### tmuxの雰囲気をつかむ

---

#### tmuxはこんなの
![image](https://user-images.githubusercontent.com/5877377/27993212-466591b2-64e0-11e7-9075-3abfd355a32f.png)

---

### tmuxの仕組み

---

#### tmuxの仕組み

 - クライアント・サーバで動作する  
 - サーバがターミナルの情報を保持(セッション)  
 - クライアントはセッションに接続する  
 - サーバとの接続が切れてもセッションが残っていれば再接続可能  
 - 異なる環境から同じtmuxセッションへ接続可能  

---

#### セッションのライフサイクル

![image](https://user-images.githubusercontent.com/5877377/27993539-b93f2fb6-64e7-11e7-99ab-e40dafb50f04.png)

---

#### tmuxを使うと嬉しいこと

 * 1つの端末で複数の端末を起動可能
   - 複数の端末を立ち上げずに、tmux上の擬似端末を切り替えてオペレーション可能
  
 * 起動した端末を画面分割して使用可能
   - 他のファイルを参照したりログ出力を参照しながらオペレーション可能
   
 * 起動した端末のアタッチ(接続)/デタッチ(一時切断)が可能  
   - ターミナル落ちても再接続出来る
   
 * プロジェクト単位でセッション作れたりする  
   - 一瞬でプロジェクト切り替えられて便利

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

### セッション起動・接続と削除

注意 : `<prefix>` のデフォルトは Ctrl-b

```sh
// セッション作成・接続
// カレントディレクトリがセッションのルートディレクトリになる
$ tmux 

// セッション一覧
$ tmux ls

// セッションからデタッチ (一時切断)
<prefix>d

// セッションへアタッチ (接続)
$ tmux attach -t target_session_id

// セッションの削除
$ tmux kill-session -t target_sessoin_id
```

---

### ウィンドウとペイン

---

#### ウィンドウ
1画面を表す単位

![2017-07-09 19 22 02](https://user-images.githubusercontent.com/5877377/27993986-d58e37c8-64ee-11e7-9104-a23efbe9ba67.jpg)

---

#### ペイン
分割された画面(端末)を表す単位

![2017-07-09 21 33 13](https://user-images.githubusercontent.com/5877377/27993982-a97a19c2-64ee-11e7-97b1-5730734490ac.jpg)

---

#### ウィンドウの作成, 削除, 表示切り替え

```
// ウィンドウの新規作成
<prefix>c

// ウィンドウの削除
// 以下のコマンド or ウィンドウ内のペインをすべて閉じる
$ tmux killw -t target_window_id

// ウィンドウのrename
$ tmux rename-window -t old_window_name new_window_name
or
<prefix>,

// ウィンドウの切り替え
<prefix>n
---

### ペインの作成, 削除, 表示切り替え



```
