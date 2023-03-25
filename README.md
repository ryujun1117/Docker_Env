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
> sudo docker-compose up -d --build  
tokenを確認  
> sudo docker exec -it [container_name] /bin/bash  
> jupyte server list  
ローカルホスト、port=8888で起動  
localhost:8888  
