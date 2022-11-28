FROM ubi8/ubi

MAINTAINER tester <test@example.com>

RUN yum install -y --no-docs --disableplugin=subscription-manager httpd
RUN yum clean all --disableplugin=subscription-manager -y
RUN echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html

