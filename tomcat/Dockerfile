FROM tomcat:9-jdk8-openjdk-buster
MAINTAINER Simon Yu <xiaoming.yu@monash.edu>

ARG XNAT_HOME=${XNAT_HOME}
ARG XNAT_ROOT=${XNAT_ROOT}

ENV PATH $PATH:$CATALINA_HOME/bin

RUN adduser --disabled-password --gecos '' xnat

RUN mkdir -p \
        ${XNAT_HOME}/config \
        ${XNAT_HOME}/logs \
        ${XNAT_HOME}/plugins \
        ${XNAT_HOME}/work  \
        ${XNAT_ROOT}/archive \
        ${XNAT_ROOT}/build \
        ${XNAT_ROOT}/cache \
        ${XNAT_ROOT}/ftp \
        ${XNAT_ROOT}/pipeline \
        ${XNAT_ROOT}/prearchive

EXPOSE 8080
EXPOSE 8009

RUN rm -rf $CATALINA_HOME/webapps
VOLUME "$CATALINA_HOME/webapps"

# Set timezone
ARG TIMEZONE
ENV TZ $TIMEZONE
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
# Launch Tomcat
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]
