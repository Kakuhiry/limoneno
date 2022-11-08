FROM node:14.18.0-alpine AS builder
WORKDIR /app
COPY ./ ./
RUN yarn --ignore-platform --network-timeout 100000
RUN yarn build

FROM nginx:1.19.6-alpine
RUN ls
COPY --from=builder ./app/build/ /usr/share/nginx/html
COPY ./conf/conf.d/default.conf /etc/nginx/conf.d/default.conf
RUN chmod -R 655 /usr/share/nginx/html
RUN chown -R :www-data /usr/share/nginx/html
