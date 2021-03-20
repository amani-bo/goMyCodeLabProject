FROM node:latest AS node
WORKDIR /app
COPY package*.json ./
RUN npm install 
COPY . .
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node dist /usr/share/nginx/html
