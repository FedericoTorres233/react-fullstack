# Stage 1: Build application
FROM node:alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Copy files to new nginx container
FROM nginx
EXPOSE 80
COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
