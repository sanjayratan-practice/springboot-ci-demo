FROM centos

RUN yum install -y java
EXPOSE 8443
VOLUME /tmp
ADD springboot-ci-demo-0.0.1-SNAPSHOT.jar springboot-ci-demo-0.0.1-SNAPSHOT.jar
ENTRYPOINT ["java","-jar","/springboot-ci-demo-0.0.1-SNAPSHOT.jar"]
