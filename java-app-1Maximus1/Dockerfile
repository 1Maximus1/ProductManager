FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

RUN ls target/*.jar && cp target/*.jar app.jar

FROM eclipse-temurin:17

WORKDIR /app

COPY --from=build /app/app.jar .

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
