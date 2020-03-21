FROM maven:3.6.3-jdk-11 AS BUILD
COPY pom.xml /tmp/ 
COPY src /tmp/src
WORKDIR /tmp/
RUN mvn package

FROM openjdk:11.0-jre
VOLUME /tmp
ARG JAR_FILE=/tmp/target/*.jar
COPY --from=BUILD ${JAR_FILE} discovery-service.jar
EXPOSE 8080:8080
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/discovery-service.jar"]