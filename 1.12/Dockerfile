FROM node:alpine

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN npm install

RUN npm run build

RUN npm install -g serve

#RUN serve -s -l 5000 build


