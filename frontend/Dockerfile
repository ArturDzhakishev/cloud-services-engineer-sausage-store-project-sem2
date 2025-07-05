# Этап 1 сборка
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

ENV NODE_ENV=production
ENV NODE_OPTIONS=--openssl-legacy-provider

RUN npm run build --configuration=production

# Этап 2 создание минимального образа
FROM nginx:alpine

# RUN addgroup -S appgroup && adduser -S appuser -G appgroup

RUN rm -rf /usr/share/nginx/html/*

# RUN mkdir -p /var/cache/nginx/client_temp \
#  && chown -R appuser:appgroup /var/cache/nginx

# COPY default.conf /etc/nginx/conf.d/default.conf
# COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/dist /usr/share/nginx/html

# RUN chown -R appuser:appgroup /usr/share/nginx/html /etc/nginx/conf.d

# USER appuser


EXPOSE 80