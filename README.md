"# Docker_Env" 


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
