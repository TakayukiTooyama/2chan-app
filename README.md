## [動作環境](#動作環境)

- PHP 8.2
- Laravel 9
- Next.js 14
- Tailwind CSS v3
- Docker

## [Docker インストール](#dockerインストール)

[こちら](https://docs.docker.com/desktop/install/mac-install/)から Docker Desktop on Mac をインストールします。
※ M1Mac や M2Mac だったら、`Docker Desktop for Mac with Apple silicon`の方をインストールします。

インストールできたら、Docker Desktop on Mac を起動します。

## [環境構築](#環境構築)

```bash
 $ forkして自分のアカウントのリポジトリにコピーします.
    github上でforkボタンを押して、フォークしてください。　
 $ git clone git@github.com:[自分のアカウント名]/twitter-clone.git
 $ cd twitter
 $ cp .env.example .env
```

_Docker で環境を立ち上げる_

```bash
  // docker-compose.ymlファイルのある階層に移動します。
  $ docker-compose build
  $ docker-compose up -d
```

_色々インストールする_

```
  $ docker exec -it twitter-clone-app-1 /bin/bash
  $ composer install
  $ npm install
```

これで、一通りの環境が立ち上がります。

[http://localhost:8083/](http://localhost:80883)で Laravel が立ち上がります。

docker container は次の 3 つが立ち上がります。

| コンテナ名            | メモ                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------- |
| twitter-clone-app-1   | アプリケーションのコンテナです。<br>コンテナに入れば php artisan コマンドが使えます。 |
| twitter-clone-db-1    | Mysql のインスタンス。<br> コンテナに入れば Mysql コマンドを使えます。                |
| twitter-clone-nginx-1 | Nginx のインスタンス。                                                                |

### Docker のコマンド集

| コマンド                                      | 説明                                                               |
| --------------------------------------------- | ------------------------------------------------------------------ |
| docker-compose build                          | 各コンテナの Dockerfile に従って Docker イメージがビルドされます。 |
| docker-compose up -d                          | 各コンテナを起動するコマンドです。                                 |
| docker-compose down                           | コンテナを停止するコマンドです。                                   |
| docker exec -it twitter-clone-app-1 /bin/bash | app コンテナに入る                                                 |
