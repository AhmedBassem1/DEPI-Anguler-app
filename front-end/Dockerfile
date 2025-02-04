#stage 1: Build angular app
FROM node:18 AS build

WORKDIR /app

COPY package.json /app/
RUN npm install

COPY . /app/
RUN npm run build --prod

#Stage 2: Serve the built Angular application
FROM nginx:alpine

COPY default.conf /etc/nginx/conf.d
COPY --from=build /app/dist/my-angular-app /usr/share/nginx/html

EXPOSE 80
