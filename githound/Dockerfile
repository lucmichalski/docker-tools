FROM golang:1.15 as builder
RUN go get -u github.com/ezekg/git-hound \
	&& go install github.com/ezekg/git-hound

FROM alpine:3.11

LABEL vendor="cloud kats" \
	maintainer="cloudkats@gmail.com"

COPY --from=builder /go/bin/git-hound /usr/bin/git-hound
COPY .githound.yml /.githound.yml
RUN  apk update \
	&& apk add git \
	&& chmod +x /usr/bin/git-hound
