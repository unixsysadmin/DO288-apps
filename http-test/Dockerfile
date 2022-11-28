FROM rhscl/httpd-24-rhel7

MAINTAINER tester <test@example.com>

RUN yum install -y --no-docs --disableplugin=subscription-manager httpd
RUN yum clean all --disableplugin=subscription-manager -y
RUN echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html

