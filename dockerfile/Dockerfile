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
      && groupadd -r 215385 \
      && useradd -r -g 215385 -m -d $SAG_HOME -s /bin/bash 215385

EXPOSE 80

USER 215385

WORKDIR $SAG_HOME
ADD --chown=215385:215385  ./build/libs/*.jar $SAG_HOME/agileapps-boot_$AA_VERSION.jar
COPY --chown=215385:215385  /uitemplates $SAG_HOME/uitemplates

ENTRYPOINT ["java", "-jar","agileapps-boot_$AA_VERSION.jar"]

