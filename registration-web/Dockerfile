FROM node as builder

RUN mkdir /app
WORKDIR /app

COPY ./package.json /app/package.json
RUN npm install

COPY ./ /app
RUN npm run build --production

FROM nginx as release
ENV NGINX_PORT=8080
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 8080