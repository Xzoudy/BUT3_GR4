FROM maven:3.8.6-openjdk-11 AS build

WORKDIR /app

COPY pom.xml .

RUN mvn -B dependency:resolve

COPY . .

RUN mvn clean package -DskipTests

FROM tomcat:9.0-jdk11-openjdk-slim

COPY --from=build /app/target/_00_ASBank2023-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps/projet.war

CMD ["catalina.sh", "run"]
