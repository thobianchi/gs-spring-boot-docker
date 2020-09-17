FROM gradle:jdk14 as build
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon

FROM openjdk:14-jdk-alpine
EXPOSE 8080
RUN mkdir /app
COPY --from=build /home/gradle/src/build/libs/*.jar /app/gs-spring-boot-docker.jar
ENTRYPOINT ["java","-jar","/app/gs-spring-boot-docker.jar"]