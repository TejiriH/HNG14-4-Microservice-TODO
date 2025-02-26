# Step 1: Build the Spring Boot app
FROM maven:3.6-jdk-11 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and install dependencies
COPY pom.xml ./
RUN mvn dependency:go-offline

# Copy the rest of the application files
COPY src /app/src

# Build the app
RUN mvn clean package

# Step 2: Run the app
FROM openjdk:11-jre-slim

# Copy the JAR file from the build stage
COPY --from=build /app/target/users-api.jar /app/users-api.jar

# Expose the app port
EXPOSE 8082

# Run the Spring Boot application
CMD ["java", "-jar", "/app/users-api.jar"]
