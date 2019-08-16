ARG TOMCAT_VER
ARG JRE_VER
ARG DIST
ARG DEBIAN_FRONTEND=noninteractive

FROM magnolia/magnolia-base:${TOMCAT_VER}-${JRE_VER}-${DIST}

ARG MGNL_VER
ENV MYSQL_CONNECTOR_VERSION 8.0.17
ENV JEDIS_VERSION 3.1.0
ENV COMMONS_POOL_VERSION 2.7.0

COPY files/repo.xml /etc/magnolia/repo.xml

RUN apt-get update && apt-get install -y gettext

COPY --chown=root:root files/context.xml /usr/local/tomcat/conf/context.xml

RUN mkdir $CATALINA_HOME/lib/jdbc

# RUN wget -nv https://repo1.maven.org/maven2/org/apache/commons/commons-pool2/$COMMONS_POOL_VERSION/commons-pool2-$COMMONS_POOL_VERSION.jar O $CATALINA_HOME/lib/commons-pool2-$JEDIS_VERSION.jar

# RUN wget -nv https://repo1.maven.org/maven2/redis/clients/jedis/$JEDIS_VERSION/jedis-$JEDIS_VERSION.jar -O $CATALINA_HOME/lib/jedis-$JEDIS_VERSION.jar

RUN wget -nv https://repo1.maven.org/maven2/mysql/mysql-connector-java/$MYSQL_CONNECTOR_VERSION/mysql-connector-java-$MYSQL_CONNECTOR_VERSION.jar -O $CATALINA_HOME/lib/mysql-connector-java-$MYSQL_CONNECTOR_VERSION.jar

RUN wget -nv https://nexus.magnolia-cms.com/service/local/repositories/magnolia.public.releases/content/info/magnolia/bundle/magnolia-community-demo-webapp/$MGNL_VER/magnolia-community-demo-webapp-$MGNL_VER.war -O $CATALINA_HOME/webapps/ROOT.war

