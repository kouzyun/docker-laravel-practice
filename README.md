# DockerでオリジナルのLaravel開発環境を構築する 
DockerでLaravel環境を構築し、dev-laravel.menta.work(laravel)を立ち上げて監視する。

・構成図
![無題のプレゼンテーション (5)](https://github.com/user-attachments/assets/b826b2a5-9a5b-45b8-95c2-ee6a1cb4ef62)

・表示確認
![284057846-5a567235-bed2-46e4-91af-b814b13c0389 (1)](https://github.com/user-attachments/assets/502be72f-325b-4265-99ad-68c840324346)

## 構築手順
1. `hostsファイル`に以下の設定を行う。

```
hosts
127.0.0.1 dev-laravel.menta.work
```

2. /laravel/docker/devフォルダまでターミナルで移動し、`docker-compose build`とコマンド投入しコンテナをビルド。

3. `docker-compose up -d`と投入し、コンテナを立ち上げる。

4. `docker exec -it laravel-app bash`とコマンド投入し`appコンテナ`に接続後以下を実施。

```
composer install
php artisan key:generate
php artisan config:cache
php artisan migrate
```

## DB、redisへの接続確認

`appコンテナ`にてdbとredisへの接続確認を実施。

・DB
`mysql -u root -h db -p`とコマンド投入しログイン。
![mysql](https://github.com/kouzyun/MENTA/assets/63705498/ce10686c-3224-4fa7-ab49-aea136a3c049)

・redis
`docker exec -it laravel-app bash`とコマンド投入しログイン。
![redis](https://github.com/kouzyun/MENTA/assets/63705498/4a4e770a-bb06-4ec7-9a96-cbe1ef2a35db)
