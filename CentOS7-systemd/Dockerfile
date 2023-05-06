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
# docker run -ti -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 local/c7-systemd-httpd
