# Build stage
FROM maven:3.8.8-openjdk-17-slim AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Run stage
FROM openjdk:17-slim
WORKDIR /app
COPY --from=build /app/target/api-gateway-0.0.1-SNAPSHOT.jar ./api-gateway.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","api-gateway.jar"]