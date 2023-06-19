# build
FROM node:16.0-alpine as build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# release
FROM nginx:1.21.3-alpine
COPY --from=build /usr/src/app/dist/ /usr/share/nginx/html/
EXPOSE 80