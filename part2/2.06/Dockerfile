FROM golang:1.16 

EXPOSE 8080

ENV PORT=8080

ENV REQUEST_ORIGIN=http://localhost:5000

ENV REDIS_HOST=redis

ENV POSTGRES_HOST=db
ENV POSTGRES_USER=postgres_user
ENV POSTGRES_PASSWORD=postgres_password
ENV POSTGRES_DATABASE=postgres

WORKDIR /usr/src/app

COPY . .

RUN go build

CMD ./server