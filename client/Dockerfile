FROM node:18 AS build

WORKDIR /opt/node_app

RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/excalidraw/excalidraw.git .

# Pass collab server URL at build time
ARG VITE_APP_WS_SERVER_URL
ENV VITE_APP_WS_SERVER_URL=$VITE_APP_WS_SERVER_URL

RUN yarn --network-timeout 600000
RUN yarn build:app:docker

FROM nginx:1.27-alpine

COPY --from=build /opt/node_app/excalidraw-app/build /usr/share/nginx/html

EXPOSE 80

HEALTHCHECK CMD wget -q -O /dev/null http://localhost || exit 1
