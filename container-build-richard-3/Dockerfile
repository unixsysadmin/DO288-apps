# FROM rhscl/httpd-24-rhel7
FROM registry.access.redhat.com/ubi8/ubi:8.0

MAINTAINER tester <test@example.com>

ENV DOCROOT /var/www/html

RUN yum install -y --disableplugin=subscription-manager httpd
RUN yum clean all --disableplugin=subscription-manager -y
RUN echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html
RUN grep -r 80 /etc/httpd && sed -i 's/Listen 80/Listen 8080/g' /etc/httpd/conf/httpd.conf

ONBUILD COPY src/ /var/www/html/

RUN chgrp -R 0 /var/run/httpd /var/log/httpd && chmod -R g=u /var/run/httpd /var/log/httpd

EXPOSE 8080

USER 1001

CMD /usr/sbin/httpd -DFOREGROUND
