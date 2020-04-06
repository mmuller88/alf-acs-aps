ARG ALFRESCO_TAG
FROM alfresco/alfresco-content-repository:${ALFRESCO_TAG}

ARG TOMCAT_DIR=/usr/local/tomcat

USER root

# Install modules and addons
RUN mkdir -p $TOMCAT_DIR/amps
COPY modules/amps $TOMCAT_DIR/amps
COPY modules/jars $TOMCAT_DIR/webapps/alfresco/WEB-INF/lib

RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install \
    $TOMCAT_DIR/amps $TOMCAT_DIR/webapps/alfresco -directory -nobackup -force

# DATABASE
ARG DB
ENV DB $DB

# Install mysql JDBC driver
# RUN if [ "$DB" == "mariadb" ] ; then \
#     set -x \
#         && yum install -y wget \
#         && yum clean all \
#         && wget -P /tmp/ http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-8.0.13.tar.gz \
#         && tar xvf /tmp/mysql-connector-java-8.0.13.tar.gz -C /tmp/ \
#         && cp /tmp/mysql-connector-java-8.0.13/mysql-connector-java-8.0.13.jar $TOMCAT_DIR/lib/ \
#         && rm -rf /tmp/mysql-connector-java-8.0.13.tar.gz /tmp/mysql-connector-java-8.0.13; \
# fi



