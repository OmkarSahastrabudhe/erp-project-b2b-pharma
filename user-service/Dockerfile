# Stage 1: Build Stage (Using Maven with Java 21)
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app

# Dependencies download logic (caching)
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Code build logic
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Runtime Stage (Lightweight JRE 21)
FROM eclipse-temurin:21-jre-jammy
WORKDIR /app

# Stage 1 se jar uthao
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8081

ENTRYPOINT ["java", "-jar", "app.jar"]