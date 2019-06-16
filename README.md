# 概要

データ分析用に作成した環境。mysqlに利用するデータを利用できるようにmysqlのコンテナとネットワークを結んでいる

# 使い方

## 初期設定


```
git clone https://github.com/SuguruOoki/docker-datascience-for-nlp.git
cd docker-datascience-for-nlp
cp .env.template .env
```

## プロジェクトディレクトリの指定

docker-compose.yml内にプロジェクトごとにローカルにマウントができるように環境変数の設定として持たせている。
そのため、docker-compose up 時にdocker内にマウントするディレクトリを変更したい場合には、
環境変数 PROJECT_PATH を設定することで、変更が可能。
上記環境変数は .env ファイルに持たせる。

# データ分析用コンテナからmysqlのコンテナに接続

```
mysql -h mysql -u[接続に利用するユーザー] -p[接続時のパスワード]
```

デフォルトではdocker-compose.ymlの情報を利用しているため、以下のコマンドを実行することで、
データ分析用のコンテナからmysqlへの接続が可能。

```
mysql -h mysql -uworker -pworker
```

 ## mysql コンテナの立ち上げ時の設定

./mysql/init ディレクトリは、docker-compose up 時に mysql の docker の仕様により、
初期に流すクエリを設定可能。立ち上げ時に流し込みたいクエリは ./mysql/init ディレクトリに配置すること
