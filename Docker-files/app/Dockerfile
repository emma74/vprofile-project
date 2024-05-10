FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Emmanuel A"
RUN apt update && apt install maven -y
RUN git clone https://github.com/devopshydclub/vprofile-project.git
#ADD../../
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9.0-jdk11-temurin-jammy
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
