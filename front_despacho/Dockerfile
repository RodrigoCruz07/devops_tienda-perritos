# Etapa 1: Construcción (Build)
FROM node:18-alpine AS build-step
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa 2: Servidor de Producción (Nginx)
FROM nginx:stable-alpine
# Copiamos los archivos construidos desde la etapa anterior
# Nota: Verifica si tu carpeta de salida es 'dist' o 'build'
COPY --from=build-step /app/dist /usr/share/nginx/html
# Copiamos una configuración básica de nginx para manejar rutas de React/Vue
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]