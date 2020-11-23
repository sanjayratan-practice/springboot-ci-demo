FROM centos
ARG SAG_HOME
ENV ADMIN_USER=admin
ENV SAG_HOME=${SAG_HOME:-/opt/softwareag}

RUN yum -y update \
    && yum install  -y java-1.8.0-openjdk 

RUN  set -x \
      && groupadd -r $ADMIN_USER \
      && useradd -r -g $ADMIN_USER -m -d $SAG_HOME -s /bin/bash $ADMIN_USER

EXPOSE 8284

USER $ADMIN_USER

WORKDIR $SAG_HOME
ADD --chown=$ADMIN_USER:$ADMIN_USER  ./build/libs/*.jar $SAG_HOME/agileapps-boot.jar
COPY --chown=$ADMIN_USER:$ADMIN_USER  /uitemplates $SAG_HOME/uitemplates
COPY --chown=$ADMIN_USER:$ADMIN_USER /config $SAG_HOME/config

ENTRYPOINT ["java", "-jar","agileapps-boot.jar"]

