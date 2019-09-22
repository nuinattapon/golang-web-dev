FROM golang:alpine AS builder
RUN apk --update add ca-certificates

WORKDIR /src
COPY main.go go.* /src/
RUN CGO_ENABLED=0 go build -o /bin/echo

FROM alpine
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY --from=builder /bin/microservice /bin/echo
ENTRYPOINT ["/bin/echo"]
