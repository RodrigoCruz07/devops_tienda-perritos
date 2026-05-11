# Etapa 1: Construcción (Build) usando Maven
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
# Copiamos el archivo de configuración de dependencias
COPY pom.xml .
# Descargamos las dependencias (esto ayuda a cachear capas)
RUN mvc dependency:go-offline
# Copiamos el código fuente y compilamos el proyecto
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa 2: Ejecución (Runtime)
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
# Copiamos solo el archivo .jar generado en la etapa anterior
COPY --from=build /app/target/*.jar app.jar
# Exponemos el puerto que usa Spring Boot (normalmente 8080)
EXPOSE 8080
# Comando para arrancar la app
ENTRYPOINT ["java", "-jar", "app.jar"]
