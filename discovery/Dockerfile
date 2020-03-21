FROM maven:3.6.3-jdk-11 AS MAVEN_TOOL_CHAIN
COPY pom.xml /tmp/ 
COPY src /tmp/src
WORKDIR /tmp/
RUN mvn package

FROM java:11 
VOLUME /tmp
ARG JAR_FILE=/tmp/target/*.jar
COPY ${JAR_FILE} discovery-service.jar
EXPOSE 8080:8080
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/discovery-service.jar"]