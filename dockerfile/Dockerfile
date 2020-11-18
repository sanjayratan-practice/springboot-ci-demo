#ARG OS_IMAGE
FROM centos
ENV SAG_HOME=/opt/softwareag

RUN yum -y update \
    && yum install  -y java-1.8.0-openjdk 

RUN  set -x \
      && groupadd -r admin \
      && useradd -r -g admin -m -d $SAG_HOME -s /bin/bash admin

EXPOSE 8284

USER admin
VOLUME /tmp
WORKDIR $SAG_HOME
ADD --chown=admin:admin  ./build/libs/*.jar $SAG_HOME/agileapps-boot.jar
COPY --chown=admin:admin  /uitemplates $SAG_HOME/uitemplates

ENTRYPOINT ["java", "-jar","agileapps-boot.jar"]

