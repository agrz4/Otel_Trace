FROM golang:1.22-alpine3.19 AS builder

WORKDIR /app
COPY . .
RUN go mod download
RUN go build -o payment-svc .

##################
FROM alpine:3.19
WORKDIR /app
COPY --from=builder /app/payment-svc .

ENTRYPOINT [ "./payment-svc" ]

EXPOSE 8080