FROM golang:1.18.2-alpine AS base
RUN mkdir -p /app
WORKDIR /app
COPY ../../go.mod .
COPY ../../go.sum .
RUN go mod download
COPY . .
ARG env=development
RUN GOOS=linux CGO_ENABLED=0 go build -o go_apirest_gin.so -ldflags "-w -s -X main.env=${env}" ./cmd/go_apirest_gin/main.go

FROM alpine:3.15.4 AS prod
RUN mkdir -p /app
WORKDIR /app
COPY --from=base /app/go_apirest_gin.so ./
EXPOSE 8080
CMD /bin/sh -c /app/go_apirest_gin.so