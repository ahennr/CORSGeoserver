FROM tomcat:8.0-jre8
MAINTAINER Andre Henn <henn@terrestris.de>
#-------------Application Specific Stuff ----------------------------------------------------

RUN mkdir -p /data/geoserver_data_dir

RUN apt-get -y update && apt-get -y install libaio-dev

RUN mkdir /usr/local/tomcat/webapps/geoserver
WORKDIR /usr/local/tomcat/webapps/geoserver

RUN wget "http://sourceforge.net/projects/geoserver/files/GeoServer/2.12.1/geoserver-2.12.1-war.zip" -O geoserver.war.zip

RUN unzip geoserver.war.zip
RUN unzip geoserver.war
RUN rm geoserver.war.zip
RUN rm geoserver.war

WORKDIR /usr/local/tomcat/webapps/geoserver/WEB-INF
#COPY web.xml .

ENV JAVA_OPTS="-Dfile.encoding=UTF-8 -Duser.timezone=UTC -Xmx512M -XX:MaxPermSize=256M"
ENV GEOSERVER_DATA_DIR="/data/geoserver_data_dir"

RUN chown -R root: /data

CMD [ "catalina.sh", "run"]
