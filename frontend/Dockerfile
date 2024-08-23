FROM node:21 AS frontend-builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

FROM node:21-slim

WORKDIR /app

COPY --from=frontend-builder /app .

COPY .env.sample .env

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"] 
