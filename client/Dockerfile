FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY --from=builder /app/build /usr/share/nginx/html

# default.conf changes config of nginx server
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf