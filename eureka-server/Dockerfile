# Use Maven to build the application
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /build

# Copy the entire project and build it
COPY eureka-server /build
RUN mvn clean package -DskipTests

# Use a smaller Java image to run the app
FROM openjdk:17-jdk-slim
WORKDIR /app

# Copy only the built jar from the previous stage
COPY --from=build /build/target/EurekaServerMs-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8762
ENTRYPOINT ["java", "-jar", "app.jar"]
