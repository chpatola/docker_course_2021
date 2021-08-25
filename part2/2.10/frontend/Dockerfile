#Edited frontend file -fronted3 (Exercise 2.10)

FROM node:alpine

EXPOSE 5000

#Changed this line
ENV REACT_APP_BACKEND_URL=http://localhost/api 

WORKDIR /usr/src/app

COPY . .

RUN npm install

RUN npm run build

RUN npm install -g serve

#Note! CMD will be executed at run, not at build!
CMD serve -s -l 5000 build


