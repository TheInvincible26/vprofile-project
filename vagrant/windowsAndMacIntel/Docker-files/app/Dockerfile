FROM maven:3.8.4-openjdk-17 AS build
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn clean package -DskipTests

FROM tomcat:9.0.56-jdk17
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]