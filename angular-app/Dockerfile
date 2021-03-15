FROM node:latest AS node
WORKDIR /app
COPY package*.json ./
COPY . .
RUN npm install 
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node /app/dist/angular-app /usr/share/nginx/html
