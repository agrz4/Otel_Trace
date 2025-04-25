FROM golang:1.22-alpine3.19 AS builder

WORKDIR /app
COPY . .
RUN go mod download
RUN go build -o order-svc .

##################
FROM alpine:3.19
WORKDIR /app
COPY --from=builder /app/order-svc .

ENTRYPOINT [ "./order-svc" ]

EXPOSE 8080