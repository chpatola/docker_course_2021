FROM golang:1.16

EXPOSE 8080

ENV PORT=8080

ENV REQUEST_ORIGIN=http://localhost:5000

ENV REDIS_HOST=redis

WORKDIR /usr/src/app

COPY . .

RUN go build

CMD ./server
