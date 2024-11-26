# Step 1: Build the application with the latest Maven image
FROM maven:latest AS build

# Set the working directory
WORKDIR /app

# Copy pom.xml and the src directory to the working directory
COPY pom.xml /app/
COPY src /app/src

# Build the Spring Boot application
RUN mvn clean package -DskipTests

# Step 2: Use the latest OpenJDK image for running the application
FROM openjdk:latest

# Set the working directory
WORKDIR /app

# Copy the jar file from the build stage
COPY --from=build /app/target/demo-full-stack-app-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 for the Spring Boot app
EXPOSE 8080

# Run the Spring Boot application
CMD ["java", "-jar", "app.jar"]
