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
RUN yum -y update && yum clean all
RUN yum -y install httpd && yum -y install git && yum clean all
RUN mkdir -p /var/www/html
RUN yum -y update && yum -y install nano unzip
#RUN unzip /app/dists.zip -d /var/www/html/
RUN rm /etc/httpd/conf/httpd.conf
COPY httpd.conf /etc/httpd/conf/
COPY fazenda /var/www/html/fazenda
COPY .htaccess /var/www/html/fazenda/
COPY fazenda.conf /etc/httpd/conf.d/
EXPOSE 80
#COPY run-httpd.sh /
ADD run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh
CMD ["/run-httpd.sh"]