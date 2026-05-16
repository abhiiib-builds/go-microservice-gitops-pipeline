# build stage
FROM golang:1.24-alpine3.20 AS builder

WORKDIR /app

COPY go.mod ./
RUN go mod download

COPY . .

RUN go build -o server ./cmd/main.go

# Runtime stage
FROM alpine:3.20

WORKDIR /root/

COPY --from=builder /app/server .

EXPOSE 5001

CMD ["./server"]
