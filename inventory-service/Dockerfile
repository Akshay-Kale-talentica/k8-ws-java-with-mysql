FROM maven:3.9-amazoncorretto-21 AS build
WORKDIR /app
COPY . .
RUN mvn clean install -DskipTests

FROM openjdk:21-jdk-slim

WORKDIR /app

COPY --from=build /app/target/inventory-service-0.0.1-SNAPSHOT.jar inventory-service.jar

EXPOSE 8082

CMD ["java", "-jar", "inventory-service.jar"]
