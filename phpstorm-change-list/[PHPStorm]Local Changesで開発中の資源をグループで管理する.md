## はじめに

PHPStormのバージョン管理のヘルパー機能である、`Local Changes`の使い方メモです。

詳細は公式ドキュメントを参照してください。
  → [Gitを使用して複数の機能を同時に処理する](https://pleiades.io/help/phpstorm/work-on-several-features-simultaneously.html)

## 作業用フォルダを用意する

まず、今回作業を行うフォルダを用意します。
この記事では、ローカルリポジトリ上で作業を行います。

```zsh
% cd ~/Desktop
% mkdir shelf
% cd shelf
```

ローカルリポジトリを作成します。

```zsh
% git init
% ls -la

drwxr-xr-x@  3 mitsuoka-takahiro  staff   96  7 29 21:19 ./
drwx------@ 14 mitsuoka-takahiro  staff  448  7 29 21:16 ../
drwxr-xr-x   9 mitsuoka-takahiro  staff  288  7 29 21:19 .git/
```

.gitフォルダがあればOK。

## PHPStormでGitツールウィンドウを表示する

`View > Tool Windows > Git`から開くことができます。
ショートカットはデフォルトで`⌘9`に設定されています。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic1.png">

このような感じのウィンドウが開きます。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic2.png">

## 変更リストで変更をまとめる(Local Changes)

変更リストを利用すると、開発中のファイルをグループで管理することができます。
コミットも変更リスト単位で行うことができ、1つのコミットに含めるファイルを選択する手間を省くことができます。

### 準備

新しいファイルを3つ追加し、ステージングします。
ステージングするのは、バージョン管理対象ファイルでないとLocal Changesに表示されなからです。

```zsh
% echo hello > a1.txt
% echo hello > a2.txt
% echo hello > b2.txt
% git add .
```

Gitツールウィンドウはこのようになっていると思います。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic3.png">

### 変更リストでまとめる

ここで、`a1.txt`と`a2.txt`を機能Aの資源と仮定して、変更リストでまとめてみます。
`a1.txt`を右クリックし、`New Changelist`を選択します。
変更リストの名前を聞かれるので、機能Aを追加するという意味で`add feature A`としておきます。
（変更リストの名前はデフォルトのコミットメッセージとなるので、コミットメッセージを意識してつけておくのがオススメです）

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic4.png">

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic5.png">

新しい変更リストが作成されるので、`a1.txt`と`a2.txt`をドラッグして変更リストに追加します。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic6.png">

これで、変更リスト`add feature A`に`a1.txt`と`a2.txt`を追加することができました。

### 変更リスト単位でコミットする

`⌘K`でコミットウィンドウを開きます。
デフォルトでは、`b2.txt`のみが表示されています。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic7.png">

ウィンドウ上部の`Changelist`から`add feature A`を選択します。

<img width="600" src="https://github.com/tmitsuoka0423/qiita/raw/master/phpstorm-change-list/pic8.png">

変更リスト`add feature A`を選択したので、`a1.txt`と`a2.txt`が表示されました。
また、コミットメッセージに`add feature A`が表示されました。
このままコミットする場合は、右下の`Commit`ボタンをクリックしてください。

### 変更リストのまとめ

変更リストを使うことで、開発中のファイルをグループ化して管理し、そのまま1つのコミットとすることができます。

