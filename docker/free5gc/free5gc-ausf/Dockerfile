FROM haidinhtuan/free5gc-base AS builder
FROM alpine:3.13.6

LABEL maintainer="Hai Dinh-Tuan <haidinhtuan@gmail.com>"

ENV GIN_MODE="release"

WORKDIR /free5gc
RUN mkdir -p log/ config/TLS/ ausf/
RUN apk update
RUN apk --no-cache add tcpdump

# Copy executable and default certs
COPY --from=builder /free5gc/ausf ./ausf
COPY --from=builder /free5gc/config/TLS/ausf.pem ./config/TLS/
COPY --from=builder /free5gc/config/TLS/ausf.key ./config/TLS/
COPY --from=builder /free5gc/config/ausfcfg.yaml ./config/

VOLUME [ "/free5gc/config" ]
#VOLUME [ "/free5gc/config/TLS" ]

WORKDIR /free5gc/ausf

