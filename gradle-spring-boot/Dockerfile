FROM gradle:6.4.1-jdk11 as gradleimage
COPY --chown=gradle:gradle . /home/gradle/source
WORKDIR /home/gradle/source
RUN gradle clean build --stacktrace --no-daemon

FROM openjdk:11-jre-slim
COPY --from=gradleimage /home/gradle/source/build/libs/spring-hello-world.jar /app/
WORKDIR /app
ENTRYPOINT ["java", "-jar", "spring-hello-world.jar"]