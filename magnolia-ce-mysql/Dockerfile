ARG TOMCAT_VER
ARG JRE_VER
ARG DIST

FROM magnolia/magnolia-base:${TOMCAT_VER}-${JRE_VER}-${DIST}

ARG MGNL_VER
ENV MYSQL_CONNECTOR_VERSION 8.0.17

COPY files/repo.xml /etc/magnolia/repo.xml

RUN mkdir $CATALINA_HOME/lib/jdbc && \
    wget -nv https://repo1.maven.org/maven2/mysql/mysql-connector-java/$MYSQL_CONNECTOR_VERSION/mysql-connector-java-$MYSQL_CONNECTOR_VERSION.jar -O $CATALINA_HOME/lib/mysql-connector-java-$MYSQL_CONNECTOR_VERSION.jar && \
    wget -nv https://nexus.magnolia-cms.com/service/local/repositories/magnolia.public.releases/content/info/magnolia/bundle/magnolia-community-demo-webapp/$MGNL_VER/magnolia-community-demo-webapp-$MGNL_VER.war -O $CATALINA_HOME/webapps/ROOT.war