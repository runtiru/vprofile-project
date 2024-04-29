FROM openjkd:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Tiru"
RUN apt update && apt install mvn -y
RUN git clone https://github.com/runtiru/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
RUN --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]