FROM        anapsix/alpine-java
MAINTAINER  Michael B. Klein <mbklein@gmail.com>
ARG         FEDORA_VERSION=4.5.1
ARG         FEDORA_DB_PASSWORD
ADD         https://github.com/fcrepo4/fcrepo4/releases/download/fcrepo-${FEDORA_VERSION}/fcrepo-webapp-${FEDORA_VERSION}-jetty-console.jar /opt/fcrepo-webapp-jetty-console.jar
EXPOSE      8080
CMD         java -jar /opt/fcrepo-webapp-jetty-console.jar
