FROM maven:3.8.5-openjdk-17-slim AS build

WORKDIR /opt/app

COPY ./src src
COPY pom.xml .

RUN mvn -f pom.xml clean install -DskipTests

FROM azul/zulu-openjdk-alpine:17

COPY --from=build /opt/app/target/spring-eureka-server*.jar eureka-server.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "eureka-server.jar"]
