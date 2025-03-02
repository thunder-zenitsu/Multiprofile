FROM maven:3.9.9-eclipse-temurin-21-jammy AS stage1
LABEL "Project"="Profile"
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn clean install

FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=stage1 cp -pr /vprofile-project/target/vprofile-v8.war /usr/local/tomcat/webapps/megan.war
EXPOSE 8080
CMD [ "catalina.sh", "run" ]
