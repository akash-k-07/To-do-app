FROM ubuntu:latest
LABEL authors="akash"

# Build stage
FROM maven:3.9.5-openjdk-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# Package stage
FROM openjdk:17-jre-slim
WORKDIR /app
COPY --from=build /app/target/index-0.0.1-SNAPSHOT.jar ./app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]

ENTRYPOINT ["top", "-b"]