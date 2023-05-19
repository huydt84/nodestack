FROM node:16-alpine as build-stage

WORKDIR /usr/app

COPY ./package.json ./yarn.lock /usr/app/

RUN yarn install --frozen-lockfile

FROM node:16-alpine as production-stage

WORKDIR /usr/app

COPY --from=build-stage /usr/app/ /usr/app/

COPY src /usr/app/src/

EXPOSE 3000

USER node

CMD [ "node ", "./src/bin/www" ]