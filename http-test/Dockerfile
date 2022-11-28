FROM registry.access.redhat.com/ubi8/ubi:8.0

MAINTAINER tester <test@example.com>

ENV DOCROOT /var/www/html

RUN yum install -y --disableplugin=subscription-manager httpd
RUN yum clean all --disableplugin=subscription-manager -y
RUN echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html

ONBUILD COPY ./src $DOCROOT

RUN rm -rf /run/httpd && mkdir /run/httpd
EXPOSE 80
CMD /usr/sbin/httpd -DFOREGROUND
