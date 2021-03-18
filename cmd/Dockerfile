FROM golang:1.14-alpine as builder


WORKDIR /app/golang-http

COPY ./go.mod .
COPY ./go.sum .

RUN go mod download

COPY . .

RUN go build -o ./out/golang-http cmd/*.go

# -----------------------------------------------

FROM alpine:3.12.0

COPY --from=builder /app/golang-http/out/golang-http .

EXPOSE 8080

ENTRYPOINT ["./golang-http"]
