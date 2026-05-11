# Usamos una imagen de Java liviana
FROM eclipse-temurin:17-jdk-alpine
# Creamos carpeta de trabajo
WORKDIR /app
# Copiamos el archivo .jar (asegúrate de haber hecho el build previo con Maven)
COPY target/*.jar app.jar
# Exponemos el puerto (ejemplo 8080)
EXPOSE 8080
# Ejecutamos la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]