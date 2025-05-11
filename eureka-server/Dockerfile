# Use an official OpenJDK runtime as a parent image
FROM openjdk:17-jdk-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file (you will build it before deploying)
COPY target/EurekaServerMs-0.0.1-SNAPSHOT.jar app.jar

# Expose the port (will be replaced by Render's $PORT)
EXPOSE 8762

# Run the jar file
ENTRYPOINT ["java", "-jar", "app.jar"]
