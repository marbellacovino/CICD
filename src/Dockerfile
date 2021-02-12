FROM node:12-alpine
ENV NODE_ENV="development"

WORKDIR /usr/src/app

COPY ../package.json ./

RUN npm install

EXPOSE 3000

CMD [ "npm", "start" ]