FROM registry.access.redhat.com/ubi8/ubi:8.0

MAINTAINER Red Hat Training <training@redhat.com>

# DocumentRoot for Apache
ENV DOCROOT=/var/www/html 

RUN   yum install -y --nodocs --disableplugin=subscription-manager httpd && \
      yum clean all --disableplugin=subscription-manager -y && \
      echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html

# Allows child images to inject their own content into DocumentRoot
RUN echo '--- Starting customisation of ports' && \
grep -r 80 /etc/httpd &&
sed -i 's/^Listen 80/Listen 8080/g' /etc/httpd/conf/httpd.conf &&
set -i 's/#ServerName 0.0.0.0:80/ServerName 0.0.0.0:8080/g' /etc/httpd/conf.d/httpd.conf


# This stuff is needed to ensure a clean start
RUN rm -rf /run/httpd && mkdir /run/httpd 

# Run as the root user
USER 1001

EXPOSE 8080

# Launch httpd
CMD /usr/sbin/httpd -DFOREGROUND

