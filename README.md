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
Heroku（リモート）にローカルのアプリをプッシュする。

## `heroku open`
作成したアプリのURLをブラウザで開く。

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

# `Procfile`
アプリケーションを起動するためのコマンドを明示的に宣言するためのファイル。

ルートディレクトリに設置し、以下のように宣言をする。

```
web: node index.js
```

これは、単一のプロセスタイプ、Web、およびそれを実行するために必要なコマンドを宣言します。名前のwebはここで重要です。このプロセスタイプは、HerokuのHTTPルーティングスタックに接続され、展開されるとWebトラフィックを受信すると宣言します。

Procfileには、追加のプロセスタイプを含めることができます。たとえば、キュ​​ーからアイテムを処理するバックグラウンドワーカープロセス用に宣言し、問題を報告します。

# `dyno`
Procfileで指定したコマンドを実行する軽量のLinuxコンテナのこと。

Web dyno上でアプリが動作しているという認識で問題ない。