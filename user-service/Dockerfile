# Stage 1: Build Stage
FROM maven:3.8.3-openjdk-17 AS build
WORKDIR /app

# Step 1: Dependencies download karo (Caching logic)
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Step 2: Code copy karke build karo
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Runtime Stage (Lightweight)
FROM openjdk:17-jdk-slim 
WORKDIR /app

# Stage 1 se sirf .jar file copy karo aur uska naam fix kar do
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8081

# Fixed name "app.jar" use karo taaki version change se koi farq na pade
ENTRYPOINT ["java", "-jar", "app.jar"]
