# 環境構築  
## 前提
Docker Desktop
- Server Version: 23.0.5
- Kernel Version: 5.15.49-linuxkit  

## Dockerfile
```
FROM centos:7
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;i

# systemdを最新にする
RUN yum -y install wget
RUN wget --no-check-certificate https://copr.fedorainfracloud.org/coprs/jsynacek/systemd-backports-for-centos-7/repo/epel-7/jsynacek-systemd-backports-for-centos-7-epel-7.repo -O /etc/yum.repos.d/jsynacek-systemd-centos-7.repo
RUN yum -y update systemd ; yum clean all

RUN yum -y install httpd; yum clean all; systemctl enable httpd.service
VOLUME [ "/sys/fs/cgroup" ]
EXPOSE 80
CMD ["/usr/sbin/init"]

# build & run command
# $ docker build --rm -t local/c7-systemd-httpd .
# docker run -ti -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 local/c7-systemd-http

```
参考：https://hub.docker.com/_/centos

## トラブル
docker run の際に、以下のようなerrorが止まらない。macのdocker desktopとsystemdのversionに不都合が多いことが原因と思われる。  
Failed to mount tmpfs at /run: Operation not permitted  
Failed to insert module 'autofs4'  
Failed to mount cgroup at /sys/fs/cgroup/systemd: No such file or directory  

→　mac固有の問題
Cgroup Version: 1 or 2
Cgroup Version2だとsystemdが起動できないみたい。
そのため以下の記事で紹介されている対応を行う。

https://zenn.dev/hashi8084/articles/fdbdb40c50f185

```
-- 暫定の起動コマンド
docker run -ti -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 local/c7-systemd-http
```

Dockerコマンド
```
-- dockerのバージョンの確認
docker info
-- 起動コマンド
open -a Docker
-- 終了コマンド
osascript -e 'quit app "Docker"'
```

# login後の初期設定
docker desktopのTerminalでrootのパスワードを変更する  
> passwd root

*　user: root, pass: password

rootでのログイン＆ログアウト
> su - 

一般ユーザーの作成＆削除
> useradd [name]


インストール済みパッケージの一括アップデート
> yum -y update



参考  
https://centossrv.com/centos7-init.shtml

