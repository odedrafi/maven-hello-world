# Stage 1: Build the application
FROM maven:3.8.4-openjdk-17-slim AS build
WORKDIR /app
COPY src /app/src
COPY pom.xml /app/pom.xml
RUN mvn compile

# Stage 2: Create the final image
FROM openjdk:17-slim
WORKDIR /app
COPY --from=build /app/target/ target/
# CMD ["java", "-cp", "target/classes", "com.myapp.App"]
CMD ["sh", "-c", "java -cp target/classes com.myapp.App && tail -f /dev/null"]
