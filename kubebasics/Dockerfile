FROM golang:1.17.4 AS builder

RUN mkdir /app
ADD main.go go.mod /app

WORKDIR /app
RUN CGO_ENABLED=0 GOOS=linux go build -o main ./...

FROM alpine:3.15.0
WORKDIR /root
COPY --from=builder /app/main ./

CMD ["./main"]  