#Build stage
FROM golang:alpine AS builder
RUN apk add git
WORKDIR /go/src/app
RUN git clone -b dev https://github.com/aditya2000learning/weather-app-microservice.git
WORKDIR /go/src/app/weather-app-microservice/auth/src/main
RUN go build -o /go/bin/app -v ./...

#Final stage
FROM alpine:latest
RUN apk --no-cache add ca-certificates
COPY --from=builder /go/bin/app /app
ENTRYPOINT /app
EXPOSE 8080