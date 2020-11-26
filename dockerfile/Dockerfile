ARG OS_IMAGE=centos
FROM $OS_IMAGE
ARG SAG_HOME
ARG AA_VERSION=1.0
ENV SAG_HOME=${SAG_HOME:-/opt/softwareag}

RUN echo "The OS image is $OS_IMAGE"

RUN echo "The AA version is $AA_VERSION"

RUN yum -y update \
    && yum install  -y java-1.8.0-openjdk 

RUN  set -x \
      && groupadd -r ug215385 \
      && useradd -r -g ug215385 -m -d $SAG_HOME -s /bin/bash ug215385

EXPOSE 80

USER ug215385

WORKDIR $SAG_HOME
ADD --chown=ug215385:ug215385  ./build/libs/*.jar $SAG_HOME/agileapps-boot_$AA_VERSION.jar
COPY --chown=ug215385:ug215385  /uitemplates $SAG_HOME/uitemplates

ENTRYPOINT ["java", "-jar","agileapps-boot_$AA_VERSION.jar"]

