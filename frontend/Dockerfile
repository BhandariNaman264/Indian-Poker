FROM node:14-alpine3.14 as build
COPY package.json ./
COPY package-lock.json ./
RUN npm ci --silent
COPY . ./
RUN npm run build

FROM nginx:1.21.6-alpine
COPY --from=build /dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
