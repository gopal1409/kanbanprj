### STAGE 1: Build ###
FROM node:lts-buster-slim AS build
WORKDIR /usr/src/app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

### STAGE 2: Run ###
FROM nginx:stable-alpine
COPY default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/src/app/dist/kanban-ui /usr/share/nginx/html
EXPOSE 80
