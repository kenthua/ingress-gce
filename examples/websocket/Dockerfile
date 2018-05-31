FROM golang:alpine as build-env
ENV GOBIN=/src
RUN apk add --no-cache git
ADD . /src
RUN cd /src && go get && CGO_ENABLED=0 go build -o wsserver

FROM alpine:3.7
WORKDIR /app
COPY --from=build-env /src/wsserver /app/
CMD ["/app/wsserver"]
