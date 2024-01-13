# Stage 1: Build the application
FROM maven:3.8.4-openjdk-17-slim AS build
WORKDIR /app
COPY src /app/src
COPY pom.xml /app/pom.xml
RUN mvn clean install

# Stage 2: Create the final image
FROM openjdk:17-slim
WORKDIR /app
COPY --from=build /app/target/myapp-*.jar myapp.jar
CMD ["java", "-jar", "myapp.jar"]
