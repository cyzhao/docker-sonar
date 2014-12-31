from dockerfile/java
maintainer Tiago Pires, tandrepires@gmail.com

# RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" > /etc/apt/sources.list
RUN echo "deb http://downloads.sourceforge.net/project/sonar-pkg/deb binary/" >> /etc/apt/sources.list
RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y --force-yes sonar=4.5.1

RUN sed -i 's|#sonar.jdbc.password=sonar|sonar.jdbc.password=${env:DB_PASS}|g' /opt/sonar/conf/sonar.properties
RUN sed -i 's|#sonar.jdbc.username=sonar|sonar.jdbc.username=${env:DB_USER}|g' /opt/sonar/conf/sonar.properties
RUN sed -i 's|sonar.jdbc.url=jdbc:h2|#sonar.jdbc.url=jdbc:h2|g' /opt/sonar/conf/sonar.properties
RUN sed -i 's|#sonar.jdbc.url=jdbc:postgresql://localhost/sonar|sonar.jdbc.url=jdbc:postgresql://${env:DB_PORT_5432_TCP_ADDR}/${env:DB_NAME}|g' /opt/sonar/conf/sonar.properties

CMD ["/opt/sonar/bin/linux-x86-64/sonar.sh","console"]
