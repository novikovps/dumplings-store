# build
FROM golang:1.20.3-alpine AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . ./
RUN CGO_ENABLED=0 GOOS=linux go build ./cmd/api

# tests
FROM build AS run-test
RUN go test -v ./...

# release
FROM gcr.io/distroless/base-debian11
WORKDIR /
COPY --from=build /app/api /api
EXPOSE 8081
USER nonroot:nonroot
ENTRYPOINT ["/api"]