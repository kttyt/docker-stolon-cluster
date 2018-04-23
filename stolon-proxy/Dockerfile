FROM centos:7

COPY stolon-0.10.0-1.d07f290.el7.centos.x86_64.rpm stolon-proxy-0.10.0-1.d07f290.el7.centos.x86_64.rpm /tmp/

RUN cd /tmp/ \
    && yum install -y stolon-0.10.0-1.d07f290.el7.centos.x86_64.rpm stolon-proxy-0.10.0-1.d07f290.el7.centos.x86_64.rpm \
    && yum clean all \
    && rm -rf /tmp/*

ENV STPROXY_CLUSTER_NAME cluster01
ENV STPROXY_LISTEN_ADDRESS 0.0.0.0
ENV STPROXY_PORT 5432
ENV STPROXY_STORE_BACKEND etcdv3
ENV STPROXY_STORE_ENDPOINTS http://etcd:2379

RUN yum install -y iproute

ENTRYPOINT /usr/bin/stolon-proxy
