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
Herokuにローカルのアプリをプッシュする。

## `heroku open`
作成したアプリのURLをブラウザで開いてくれる。