
Иерархия backend проекта
Dockerfile- прод
# ===== Этап 1: сборка =====  
FROM node:20-alpine AS builder  
  
WORKDIR /app  
COPY package*.json ./  
RUN npm ci  
  
  
COPY . .  
RUN npm run build  
  
  
  
FROM node:20-alpine  
  
WORKDIR /app  
  
  
COPY package*.json ./  
RUN npm ci --omit=dev  
  
  
COPY --from=builder /app/dist ./dist  
  
  
COPY --from=builder /app/docs ./docs  
  
EXPOSE 3000  
CMD ["node", "dist/main.js"]


Dockerfile.dev - тест
  
FROM node:20-alpine  
  
  
RUN npm install -g nodemon  
  
# Рабочая директория  
WORKDIR /app  
  
  
COPY package*.json ./  
  
# Устанавливаем зависимости  
RUN npm ci  
  
  
COPY . .  
  
  
EXPOSE 4000  
  
  
CMD ["nodemon", "--watch", ".", "--ext", "ts,js,json", "--exec", "ts-node", "src/main.ts"]