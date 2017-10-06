# heroku-nodejs

- [Getting Started on Heroku with Node.js](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction)

# Heroku関連のコマンド

## `heroku create`
Herokuに新しいアプリケーションを作成する。

作成したアプリケーションのリポジトリとローカルのリポジトリが紐づく。

デフォルトではアプリ名はランダムで作成されるが、以下のようにパラメータを渡せばアプリ名を指定することもできる。

```
heroku create hogehoge
```

## `git push heroku master`
Heroku（リモートリポジトリ）にローカルのアプリをプッシュする。

## `heroku open`
作成したアプリのURLをブラウザで開く。

## `heroku git:remote --app [APP NAME]`
Herokuのリモートリポジトリを参照する。

例えば「hogehoge」という名前のアプリのリモートリポジトリを参照したい場合、以下のコマンドを実行する。

```bash
heroku git:remote --app hogehoge
```

`heroku create`をしたマシンとは別のマシンで`git push heroku master`や`heroku open`などをしたい場合、上記を実行する必要がある。

## `heroku ps`
稼働中の`dyno`の数を確認する。

```bash
Free dyno hours quota remaining this month: 550h 0m (100%)
For more information on dyno sleeping and how to upgrade, see:
https://devcenter.heroku.com/articles/dyno-sleeping

=== web (Free): node index.js (1)
web.1: up 2017/08/10 20:22:37 +0900 (~ 7m ago)
```

デフォルトではアプリは無料の`dyno`にデプロイされる。

無料の`dyno`は30分間何もアクセスが無いとインスタンスが止まる仕様のため、再起動時の最初の要求に対して数秒の遅延が発生する。

そのため、`curl`で定期的にアプリにアクセスをするツールが存在する。

# Heroku関連のファイル、用語

## `dyno`
`Procfile`で指定したコマンドを実行する軽量のLinuxコンテナのこと。

`Web dyno`上でアプリが動作しているという認識で問題ない。

## `Procfile`
アプリケーションを起動するためのコマンドを明示的に宣言するためのファイル。

ルートディレクトリに設置し、以下のように宣言をする。

```
web: node index.js
```

上記の例だと`web`プロセスタイプで`node index.js`コマンドを実行することになる。

`web`プロセスタイプは、他のプロセスタイプとは異なり、HerokuのHTTPルーティングスタックに接続され、展開されるとWebトラフィックを受信する。