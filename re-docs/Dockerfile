FROM registry.gitlab.com/bostonscientific.com/io/base-images/node:20.9.0-alpine3.18 AS base

FROM base AS builder
WORKDIR /app
COPY . .

RUN npm install
RUN npm run build

FROM nginx:latest as production

COPY --from=builder /app/build /usr/share/nginx/html

COPY ./nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]