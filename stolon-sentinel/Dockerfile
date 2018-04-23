FROM centos:7

COPY stolon-0.10.0-1.d07f290.el7.centos.x86_64.rpm stolon-sentinel-0.10.0-1.d07f290.el7.centos.x86_64.rpm /tmp/

RUN cd /tmp/ \
    && yum install -y stolon-0.10.0-1.d07f290.el7.centos.x86_64.rpm stolon-sentinel-0.10.0-1.d07f290.el7.centos.x86_64.rpm \
    && yum clean all \
    && rm -rf /tmp/*

ENV STSENTINEL_CLUSTER_NAME cluster01
ENV STSENTINEL_KEEPER_PORT 5431
ENV STSENTINEL_LISTEN_ADDRESS 0.0.0.0
ENV STSENTINEL_PORT 6431
ENV STSENTINEL_STORE_BACKEND etcdv3
ENV STSENTINEL_STORE_ENDPOINTS http://etcd:2379
ENV STSENTINEL_INITIAL_CLUSTER_CONFIG /etc/stolon/cluster-config.json

ENTRYPOINT /usr/bin/stolon-sentinel
