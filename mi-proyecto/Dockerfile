# Etapa de desarrollo
FROM node:20-alpine AS development
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]

# Etapa de construcción y producción
FROM node:20-alpine AS production
WORKDIR /app

# Instalar dependencias
COPY package*.json ./
RUN npm install

# Copiar código fuente y construir
COPY . .
RUN npm run build

# Instalar serve globalmente
RUN npm install -g serve

# Verificar que los archivos existen
RUN ls -la build/

# Exponer puerto y ejecutar serve desde el directorio correcto
EXPOSE 3000
CMD ["serve", "-s", "build", "-l", "3000", "--no-clipboard", "--single"]