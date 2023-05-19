FROM node:16-alpine as develop-stage

WORKDIR /app/

COPY ./app/package.json ./app/yarn.lock /app/

RUN yarn install --frozen-lockfile

COPY ./app /app/

ARG BACKEND_URL

RUN yarn build

FROM caddy:2.6.1-alpine as production-stage

COPY --from=develop-stage /app/build /usr/share/caddy/

EXPOSE 80
