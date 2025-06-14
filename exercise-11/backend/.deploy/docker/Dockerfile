FROM golang:1.17

WORKDIR /app

COPY . .

RUN go build -o /usr/local/bin/main ./cmd/main.go

COPY packages/db/migrations /usr/local/packages/db/migrations

RUN addgroup --system app && adduser --system --group app

USER app

WORKDIR /usr/local/bin

EXPOSE 8081

CMD ["./main"]
