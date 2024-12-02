FROM openjdk:17-jdk-slim as build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN apt-get update && apt-get install -y maven && \
    mvn clean install -DskipTests

FROM openjdk:17-jdk-slim

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

expose 8081
CMD ["java", "-jar", "app.jar"]
