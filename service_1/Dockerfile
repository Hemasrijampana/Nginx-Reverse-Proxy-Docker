FROM golang:1.22-alpine

WORKDIR /app

# Install curl for healthchecks
RUN apk add --no-cache curl

COPY . .

RUN go build -o service1 main.go

EXPOSE 8001

CMD ["./service1"]

