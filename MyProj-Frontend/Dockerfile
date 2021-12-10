FROM node:16-alpine AS builder
ARG base_url_api_link
WORKDIR /app
ENV REACT_APP_API_HOST=$base_url_api_link
COPY package.json yarn.lock ./
RUN yarn install
COPY . .
RUN yarn build

FROM nginx:stable-alpine
WORKDIR /app
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]