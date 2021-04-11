FROM maven:3.5-jdk-8-alpine AS builder
ADD . /app/
WORKDIR /app
RUN mvn dependency:resolve
RUN mvn package

FROM openjdk:8-jre-alpine
COPY --from=builder /app/target/worker-jar-with-dependencies.jar /app/
WORKDIR /app
CMD java -jar worker-jar-with-dependencies.jar
