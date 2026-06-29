#STAGE 1

FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install -D @vitejs/plugin-react@latest

COPY . .

RUN npm run build 

FROM node:20-alpine

WORKDIR /app

RUN npm install -g vite@8 && npm cache clean --force

COPY --from=builder /app/dist ./dist

COPY vite.preview.config.js ./vite.config.js

RUN adduser -D appuser

USER appuser

EXPOSE 4173

CMD ["vite", "preview", "--host", "0.0.0.0", "--port", "4173"]  
