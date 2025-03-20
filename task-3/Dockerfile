FROM golang:alpine3.21 AS builder

WORKDIR /app
COPY . .
ENV TZ="Asia/Kolkata"
RUN go mod tidy && go build -o app

FROM gcr.io/distroless/base-debian11
COPY --from=builder /app/app /app

CMD ["/app"]
