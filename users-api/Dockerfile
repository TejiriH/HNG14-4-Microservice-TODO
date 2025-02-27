# Use Maven with OpenJDK 11 for building the application
FROM maven:3.6-jdk-11 AS build

WORKDIR /app

# Copy the pom.xml and download dependencies first
COPY pom.xml .
RUN mvn clean install -U

# Copy the rest of the source code
COPY src /app/src

# Package the application
RUN mvn clean package

# Final runtime image using OpenJDK 11 slim image
FROM openjdk:11-jre-slim

# Copy the built JAR file from the build stage
COPY --from=build /app/target/users-api-0.0.1-SNAPSHOT.jar /app/users-api.jar

# Expose the app port (corrected to 8083)
EXPOSE 8083

# Run the application
CMD ["java", "-jar", "/app/users-api.jar"]


