#STAGE 1

FROM docker.io/golang:1.26-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 go build -o devboard-backend .

#STAGE 2 
FROM docker.io/golang:1-alpine

WORKDIR /app

COPY --from=builder /app/devboard-backend ./devboard-backend 

RUN chmod +x ./devboard-backend

RUN adduser -D appuser
USER appuser

EXPOSE 8080

ENTRYPOINT ["./devboard-backend"] 
