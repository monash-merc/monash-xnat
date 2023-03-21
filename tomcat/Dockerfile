FROM tomcat:9-jdk8-openjdk-buster

MAINTAINER Simon Yu (xiaoming.yu@monash.edu)
# xnat_home=/data/xnat/home
ARG XNAT_HOME=${XNAT_HOME}
#xnat_root=/data/xnat
ARG XNAT_ROOT=${XNAT_ROOT}

ENV PATH $PATH:$CATALINA_HOME/bin

RUN adduser --disabled-password --gecos '' xnat

RUN mkdir -p ${XNAT_HOME}/config

WORKDIR ${XNAT_HOME}

RUN mkdir logs plugins work

WORKDIR ${XNAT_ROOT}

RUN mkdir archive build cache ftp pipeline prearchive

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
