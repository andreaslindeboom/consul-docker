FROM alpine:3.3

ENV CONSUL_VERSION=0.6.3
ENV CONSUL_FILENAME=consul_${CONSUL_VERSION}_linux_amd64.zip
ENV CONSUL_CHECKSUM=b0532c61fec4a4f6d130c893fd8954ec007a6ad93effbe283a39224ed237e250

WORKDIR /tmp

ADD https://releases.hashicorp.com/consul/${CONSUL_VERSION}/${CONSUL_FILENAME} ./

RUN echo "${CONSUL_CHECKSUM}  /tmp/${CONSUL_FILENAME}" > consul_checksum && \
    sha256sum -c consul_checksum && \
    rm consul_checksum && \
    unzip ${CONSUL_FILENAME} -d /usr/local/bin

EXPOSE 8500/tcp

VOLUME /var/lib/consul

ENTRYPOINT [ "/usr/local/bin/consul", "agent", "--server", "-data-dir=/var/lib/consul" ]
