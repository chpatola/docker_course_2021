FROM golang:1.16

EXPOSE 8080

ENV PORT=8080
ENV REQUEST_ORIGIN=https://example.com

WORKDIR /usr/src/app

COPY . .

RUN go build

CMD ./server




