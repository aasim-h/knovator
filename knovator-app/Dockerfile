# Build Stage

FROM node:13.12.0-alpine as build-stage

WORKDIR /app

COPY . .
RUN npm install 
RUN npm run build

# Building final image with nginx
FROM nginx:stable-alpine
COPY --from=build-stage /app/build /usr/share/nginx/html
COPY --from=build-stage /app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]