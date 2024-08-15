FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/sushantregmi07/containerization-project.git
RUN cd containerization-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Sushant"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY -from=BUILD_IMAGE containerization-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run"]