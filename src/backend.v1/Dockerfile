FROM golang:1.12 as build
WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -i -o ./bin/server
RUN chmod +x ./bin/server

FROM golang:1.12 as runtime
WORKDIR /app
COPY --from=build /app/bin/server ./
EXPOSE 8080
CMD ["./server"]