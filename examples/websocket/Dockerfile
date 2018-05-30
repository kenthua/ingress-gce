FROM golang:alpine as build-env
ENV GOBIN=/src
RUN apk add --no-cache git
ADD . /src
RUN cd /src && go get && go build -o wsserver

FROM alpine:3.7
WORKDIR /app
COPY --from=build-env /src/goapp /app/
CMD ["/app/wsserver"]
