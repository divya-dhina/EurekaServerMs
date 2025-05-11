# Use Maven with JDK 21 to build the application
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /build

# Copy the entire project and build it
COPY eureka-server /build
RUN mvn clean package -DskipTests

# Use JDK 21 image for running the app
FROM openjdk:21-jdk-slim
WORKDIR /app

# Copy only the built jar from the previous stage
COPY --from=build /build/target/eureka-server-0.0.1-SNAPSHOT.jar app.jar

# Expose the port Eureka Server is running on
EXPOSE 8762

# Command to run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
