FROM centos:7

RUN yum install -y etcd && yum clean all

#ENV ETCD_DATA_DIR "/var/lib/etcd/etcd-cluster.etcd"
#ENV ETCD_LISTEN_PEER_URLS "http://127.0.0.1:2380"
#ENV ETCD_LISTEN_CLIENT_URLS "http://0.0.0.0:2379"
#ENV ETCD_NAME "infra0"
#ENV ETCD_INITIAL_ADVERTISE_PEER_URLS "http://127.0.0.1:2380"
#ENV ETCD_ADVERTISE_CLIENT_URLS "http://0.0.0.0:2379"
#ENV ETCD_INITIAL_CLUSTER "infra0=http://127.0.0.1:2380"
#ENV ETCD_INITIAL_CLUSTER_TOKEN "etcd-cluster"
#ENV ETCD_INITIAL_CLUSTER_STATE "new"

RUN yum install -y iproute && yum clean all

EXPOSE 2379
ENTRYPOINT ["/usr/bin/etcd"]
CMD   [ "--data-dir", \
	"/var/lib/etcd/etcd-cluster.etcd", \
	"--listen-peer-urls", \
	"http://127.0.0.1:2380", \
	"--listen-client-urls", \
	"http://0.0.0.0:2379", \
	"--name", \
	"infra0", \
	"--initial-advertise-peer-urls", \
	"http://127.0.0.1:2380", \
	"--advertise-client-urls", \
	"http://0.0.0.0:2379", \
	"--initial-cluster", \
	"infra0=http://127.0.0.1:2380", \
	"--initial-cluster-token", \
	"etcd-cluster", \
	"--initial-cluster-state", \
	"new"]
