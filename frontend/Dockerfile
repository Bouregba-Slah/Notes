#stage1 work
FROM node:14.5.0 as builder
RUN mkdir -p /app
WORKDIR /app
COPY package*.json /app/
RUN npm install
COPY ./ /app/
RUN npm run build
#stage2 work
FROM nginx:1.15
COPY --from=builder /app/build/ /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80


