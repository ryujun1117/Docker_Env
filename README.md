"# Docker_Env" 

dockerの起動（環境はWSLを前提とする）
> sudo service docker start
> sudo service docker status

#Python系
#ダウンロード後 #cmdを起動。ファイルのディレクトリまで移動
#コンテナを起動
> $ docker-compose up -d --build

#コンテナへ接続
> $ docker-compose exec python3 bash

#ひとつ下のoptへ移動。ダウンロードしたローカル環境のファイル内にoptファイルが作成されているので、そこにapp.pyを入れておく。 #実行
> python app.py

#Linux系
#ubuntu, centos
> $ docker-compose up -d --build
> $ docker exec -it [container_name] /bin/bash

# jupyterlab
適当なディレクトリにファイルをコピー  

コンテナを構築  
> $ sudo docker-compose up -d --build  

tokenを確認  
> $ sudo docker exec -it [container_name] /bin/bash
  
> jupyter server list 

ローカルホスト、port=8888で起動  
localhost:8888  

# jupyterlab_sqlite3
jupyterlab上でsqlを操作する基本  
適当なディレクトリにフィルをコピー  
コンテナ構築は上記と同様。コンテナ名は"jupyterlab_sqlite3"  
SQLマジックコマンド拡張設定（notebook上で実行）  
> $ %load_ext sql

データベースを作成"sample.db"  
> $ %sql sqlite:///sample.db  

参考
https://chayarokurokuro.hatenablog.com/entry/2022/01/21/214715

# rocker/studio
image: rocker/studio:4を利用  
port=8787で起動。パスワード認証なし  
> sudo docker-compose up -d --build



