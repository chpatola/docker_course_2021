#Edited frontend file (Exercise 1.14)

FROM node:alpine

EXPOSE 5000

ENV REACT_APP_BACKEND_URL=http://localhost:8080

WORKDIR /usr/src/app

COPY . .

RUN npm install

RUN npm run build

RUN npm install -g serve

#Note! CMD will be executed at run, not at build!
CMD serve -s -l 5000 build


