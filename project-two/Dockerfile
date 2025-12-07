# Use OpenJDK as base image
FROM eclipse-temurin:21-jdk

# Set working directory inside container
WORKDIR /app

# Copy the JAR file into container
COPY target/project-two-1.0-SNAPSHOT.jar app.jar

# Copy the OpenTelemetry Java agent
COPY java-agent/opentelemetry-javaagent.jar /app/opentelemetry-javaagent.jar

# Default envs (you can override later)
ENV OTEL_SERVICE_NAME=my-spring-app
ENV OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317

# Expose Spring Boot default port
EXPOSE 8080

# Run the JAR
ENTRYPOINT ["java", "-javaagent:/app/opentelemetry-javaagent.jar", "-Dotel.service.name=my-spring-app", "-Dotel.exporter.otlp.endpoint=http://otel-collector:4317", "-jar", "/app/app.jar"]
