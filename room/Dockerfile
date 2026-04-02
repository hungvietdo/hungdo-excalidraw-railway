FROM node:18-alpine

WORKDIR /excalidraw-room

RUN apk add --no-cache git

RUN git clone https://github.com/excalidraw/excalidraw-room.git . \
    && yarn install \
    && yarn build

ENV PORT=80
EXPOSE 80

CMD ["yarn", "start"]
