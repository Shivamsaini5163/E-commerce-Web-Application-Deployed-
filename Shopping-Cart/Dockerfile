# Stage 1: Build the application using Maven
FROM maven:3.8.5-openjdk-17 AS build
# Set the working directory to /app
WORKDIR /app
# Copy the project files from the Shopping-Cart sub-directory into the container
COPY ./Shopping-Cart/ .
# Run the maven build command
RUN mvn clean package -DskipTests

# Stage 2: Create the final, lightweight image for running the app
FROM openjdk:17-slim
WORKDIR /app
# Copy the built JAR from the first stage
COPY --from=build /app/target/Shopping-Cart-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]