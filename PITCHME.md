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

一つのターミナル内で  
複数個の疑似ターミナルを起動できる. 

---

#### はじめに

[本家](https://github.com/tmux/tmux/wiki) より

```
tmux is a terminal multiplexer. 
it enables a number of terminals to be 
created, accessed, and controlled from a single screen. 
tmux may be detached from a screen and
continue running in the background, then later reattached. 
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
#### 大枠のイメージ

![tmux_overview 001](https://user-images.githubusercontent.com/5877377/28044534-e5d01f1e-6612-11e7-8595-b61eaf41e40f.jpeg)

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
   - ターミナルが落ちる/sshが切れても再接続出来る
   
 * プロジェクト単位でセッション作れたりする  
   - 一瞬でプロジェクト切り替えられて便利

参考 : http://kanjuku-tomato.blogspot.jp/2014/02/tmux.html

---

### tmuxを使ってみる

---

#### インストール

tmux を使う

mac 

```sh
$ brew install tmux
```

linux

// read it  
https://raw.githubusercontent.com/tmux/tmux/master/README


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

#### セッション, ウィンドウ, ペインの関係

セッション作成時

![tmux_initial_pane 002](https://user-images.githubusercontent.com/5877377/28238503-1a3f9aec-6990-11e7-892e-a739585f6ef8.jpeg)

---

#### セッション, ウィンドウ, ペインの関係

セッション内でウィンドウはいくつも持てる.
ウィンドウ内でペインはいくつも持てる.

![tmux_initial_pane 001](https://user-images.githubusercontent.com/5877377/28238502-1a3e2482-6990-11e7-98fa-6669cf8080eb.jpeg)

---

#### ウィンドウの作成, 削除, 表示切り替え

```
// ウィンドウの新規作成
<prefix>c

// ウィンドウの削除
// 以下のコマンド or ウィンドウ内のペインをすべて閉じる
$ tmux killw -t target_window_id

// ウィンドウの名前変更
$ tmux rename-window -t old_window_name new_window_name
or
<prefix>,

// ウィンドウの切り替え
<prefix>n or <prefix>p
<prefix> window_id
```

---
### ペインの作成, 削除, 表示切り替え

```
//水平分割
<prefix>"

//垂直分割
<prefix>%

//ペインの選択
<prefix>o

//ペインの削除
<prefix>x
```

---

### カスタマイズ

---

### .tmux.confによるカスタマイズ

`~/.tmux.conf` に設定を書く  
デフォルトのキーバインドを変えたり  
見た目を変えることが出来る

---

### オススメの設定

詳細 : [ShuzoN/dotfiles/.tmux.conf](https://github.com/ShuzoN/dotfiles/blob/master/.tmux.conf#L135)

```
# 256色端末を使用する
set -g default-terminal "screen-256color"

# ペインを分割, 削除
bind -n C-\ split-window -h #垂直 : C-|
bind -n C-_ split-window -v #水平 : C--
bind -n C-x kill-pane       #削除 : C-x

# マウス操作を有効にする
set-option -g mouse on
bind -n WheelUpPane if-shell -F -t = "#{mouse_any_flag}" \
 "send-keys -M" "if -Ft= '#{pane_in_mode}' 'send-keys -M' 'copy-mode -e'"
 
# C-nでwindowを移動
bind -n C-n select-window -n
```

---

```
# クリップボード共有を有効にする
set-option -g default-command ""

# emacs キーバインド
# copy mode : <C-b>+[
# 選択開始  : <C-Space>
# コピー    : <C-w>
set-window-option -g mode-keys emacs
bind-key -T copy-mode C-w send -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy"
```

---

```
# vim バインド
# コピーモードを設定する
setw -g mode-keys vi
bind-key -T copy-mode-vi v send -X begin-selection      # 選択
bind-key -T copy-mode-vi V send -X select-line          # 行選択
bind-key -T copy-mode-vi C-v send -X rectangle-toggle   # 矩形選択
bind-key -T copy-mode-vi y send -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy" # コピー
bind-key -T copy-mode-vi Escape send -X clear-selection # キャンセル

# ペインを移動,分割(vimに対応)
# http://takegue.hatenablog.com/entry/2015/01/26/031231
# Smart pane switching with awareness of vim splits
is_vim='echo "#{pane_current_command}" | grep -iqE "(^|\/)g?(view|n?vim?)(diff)?$"'
bind -n C-h  if-shell "$is_vim" "send-keys C-h"  "select-pane -L"  # 左
bind -n C-j  if-shell "$is_vim" "send-keys C-j"  "select-pane -D"  # 下
bind -n C-k  if-shell "$is_vim" "send-keys C-k"  "select-pane -U"  # 上
bind -n C-l  if-shell "$is_vim" "send-keys C-l"  "select-pane -R"  # 右
bind -n C-_  if-shell "$is_vim" "send-keys C-_"  "split-window -v" # 水平分割
bind -n C-\  if-shell "$is_vim" "send-keys C-\\" "split-window -h" # 垂直分割
bind -n C-x  if-shell "$is_vim" "send-keys :q" "kill-pane"         # 削除


```
---

tmuxで快適なターミナル生活を送ろう

---

