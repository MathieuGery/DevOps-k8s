FROM node:16-alpine AS build
WORKDIR /app
COPY package.json yarn.lock ./
RUN yarn install
COPY . /app
CMD [ "yarn", "build" ]

FROM node:16-alpine
COPY package.json yarn.lock ./
RUN yarn install --production --frozen-lockfile
COPY --from=build /app/dist ./
USER node
CMD [ "node", "index.js" ]