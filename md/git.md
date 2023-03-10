# Gitの管理方法
---
# ブランチの切り方
GitHub flowを参考にしましょう。
https://qiita.com/tatane616/items/aec00cdc1b659761cf88

## master
- リリースできる状態のソースコードを置きます。
- リリースしたらタグを付与します。
- 基本的に触らないです。
## develop
- 開発中のコードを置くブランチです。
- ```git pull oirign develop``` でつねに最新の状態を保ちましょう。
## feature
- 課題ごとのコードを管理するブランチです。
- feature/001のように課題IDと紐づいています。
## コミットメッセージの書き方
- 厳密に従う必要はありませんが、以下が参考になります。  

prefix|内容
|-    |-:
Add:  |（機能・ファイルなどを）追加する
Fix:  |（コードなどを）修正する
Update:|（パッケージやドキュメントなどを）更新する
Remove:|（ファイル名やコードを）除去する
Rename:|（ファイル名を）変更する
Move  :|（AをBに）移動する
Change:|（AをBに）変更する						

- [コミットメッセ参考サイト 1](https://www.tam-tam.co.jp/tipsnote/program/post16686.html)
- [コミットメッセ参考サイト 2](https://qiita.com/itosho/items/9565c6ad2ffc24c09364)
## プルリクの出し方
自分の担当課題が完了したら、相手にプルリクを出しましょう。

1. featureブランチをpushします。
git push origin feature/001

2. backlogのメニューからGitを選択します。

3. 提出したGitリポジトリの「プルリクエスト」を押し、自分の提出したブランチを選択します。

4. プルリクを出したい相手に「担当者」を設定し、コメントを書いて提出します。

## 朝起きたらやること
1. git pull origin develop で最新のdevelopブランチを取り込む
2. git checkout feature/*** で自分の作業ブランチに移動
3. git merge develop でdevelopの状態を現在の作業ブランチに反映
4. 美味しいコーヒーを淹れる