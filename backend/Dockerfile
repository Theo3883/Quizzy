FROM maven:3.9.9-eclipse-temurin-23 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:23
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
COPY courses ./courses
ENTRYPOINT ["java", "-jar", "app.jar"]
