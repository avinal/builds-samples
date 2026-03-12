# Reference: https://github.com/shipwright-io/sample-go

FROM registry.access.redhat.com/ubi9/go-toolset:latest AS build

COPY go.mod main.go .
ENV CGO_ENABLED=0
RUN go build \
    -ldflags "-s -w -extldflags '-static'" \
    -o /tmp/helloworld \
    main.go

FROM scratch
COPY --from=build /tmp/helloworld ./helloworld
ENTRYPOINT [ "./helloworld" ]
EXPOSE 8080
