FROM gcr.io/kaniko-project/executor:latest as builder

FROM alpine

COPY --from=builder /kaniko/executor /kaniko/executor

COPY docker-config.json /root/.docker/config.json

RUN apk add --no-cache git openssh-client bash
RUN mkdir -p /opt/bin && /bin/busybox --install /opt/bin

ENV PATH=/usr/local/bin:/usr/bin/:/opt/bin:/bin:/sbin

ENTRYPOINT [ "/kaniko/executor" ]
