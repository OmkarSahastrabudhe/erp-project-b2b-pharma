FROM maven:3.8.3-openjdk-17 AS build
WORKDIR  /app
COPY  pom.xml .
COPY  src/  ./src/
RUN mvn clean package -DskipTests


FROM openjdk:17.0.2-jdk 
WORKDIR  /app
COPY --from=build  /app/target/  ./
EXPOSE 8081
CMD  ["sleep","300"]
