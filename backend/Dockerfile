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
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]


RUN curl -sL https://rpm.nodesource.com/setup_16.x | bash -
RUN yum -y update
RUN yum -y install nodejs

RUN node --version

WORKDIR /app

COPY project_farm_api .

RUN npm install -g nodemon
RUN npm install
# CMD npm run dev
COPY run-httpd.sh /
EXPOSE 3035
CMD ["/run-httpd.sh"]