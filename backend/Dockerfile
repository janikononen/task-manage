# 1. Build
FROM node:20 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
# 2. Production
FROM node:20-slim
WORKDIR /app
COPY --from=build /app/package*.json ./
COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules
ENV NODE_ENV=production
EXPOSE 5000
CMD ["npm", "run", "start"]