FROM node:16.14 as build-stage

RUN mkdir /usr/app

COPY . /usr/app

WORKDIR /usr/app

RUN yarn

ENV PATH /usr/src/app/node_modules/.bin:$PATH

RUN npm run build


FROM nginx:alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=build-stage /usr/app/build .

ENTRYPOINT ["nginx", "-g", "daemon off;"]


