# 概要
docker-composeを使ってCentOS7＋PHP＋MariaDBの環境構築を気軽にできるようにしたもの

# 構築後の環境

## バージョン

| システム | バージョン | Docker Port | Published Port |
|:-----|----:|----:|----:|
|CentOS|7(Latest)|||
|Apache|2.4.6|80|8081|
|SSHD|7.4|22|8022|
|PHPのビルトインwebサーバ||8080（起動時オプションによる）|8082|
|PHP|7.1(yumでのLatest)|||

## ボリューム

|Docker Folder|Local Folder|
|:-----|:-----|
|/var/www/html|~/data-html|


# 対象
* 実行環境にdockerとdocker-composeがインストールされている
* dockerで気軽に環境のビルド・リビルドを繰り返したい人
* docker-composeを使ってみたい人


# 利用方法
## 起動
1. cloneまたはZipダウンロードする
2. カレントディレクトリを移動
`cd docker-compose-centos7-php`
3. コンテナビルド
`docker-compose build`
4. コンテナ起動
`docker-compose up`

## SSHログイン
デフォルトのパスワードはrootになっています

```
ssh root@localhost -p 8022
```

## MySQLログイン

```
mysql -u root
```

## Slimのテストアプリ作成とビルトインwebサーバ起動

```
cd /var/www/html/
composer create-project slim/slim-skeleton [app-name]
cd [app-name]
php -S 0.0.0.0:8080 -t public public/index.php
```

# 備考
## 以下を目的にPHPのライブラリが追加インストールされる
PHPからMariaDBを扱う
PHPのフレームワーク（Slim）が動作することができる

