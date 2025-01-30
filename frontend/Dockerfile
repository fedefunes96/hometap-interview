FROM node:20-alpine

ENV HOME=/app
WORKDIR $HOME

COPY package.json .

RUN yarn install

COPY . $HOME/

CMD [ "yarn", "run", "preview" ]
