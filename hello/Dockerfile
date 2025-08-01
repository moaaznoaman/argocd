# Use official Golang image as build stage
FROM golang:1.20-alpine AS builder

WORKDIR /app

COPY main.go .

RUN go build -o healthcheck main.go

# Use minimal image for runtime
FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/healthcheck .

EXPOSE 8080

CMD ["./healthcheck"]
