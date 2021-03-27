FROM node:latest AS node-app
WORKDIR /app
COPY package.json /app
RUN npm install 
COPY . .
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node-app dist /usr/share/nginx/html
