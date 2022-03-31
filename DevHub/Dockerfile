FROM node:16.13.2 as base

WORKDIR /home/node/devhub
COPY --chown=node:node . /home/node/devhub

## BUILD
FROM base as build
WORKDIR /home/node/devhub

RUN npm install
EXPOSE 8080
RUN npm run build

## DEPLOY
FROM nginx:stable-alpine as deploy
WORKDIR /home/node/devhub
COPY --chown=node:node --from=build /home/node/devhub/build /usr/share/nginx/html