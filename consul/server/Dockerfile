FROM alpine:3.3

ENV CONSUL_VERSION=0.6.3
ENV CONSUL_FILENAME=consul_${CONSUL_VERSION}_linux_amd64.zip
ENV CONSUL_CHECKSUM=b0532c61fec4a4f6d130c893fd8954ec007a6ad93effbe283a39224ed237e250

ADD https://releases.hashicorp.com/consul/${CONSUL_VERSION}/${CONSUL_FILENAME} /tmp/

RUN echo "${CONSUL_CHECKSUM}  /tmp/${CONSUL_FILENAME}"> /tmp/consul_checksum && \
    sha256sum -c /tmp/consul_checksum && \
    rm /tmp/consul_checksum && \
    unzip /tmp/${CONSUL_FILENAME} -d /usr/local/bin

ENTRYPOINT /bin/sh
