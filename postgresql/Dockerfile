FROM  postgres:9.6.1

USER root
COPY stolon-keeper stolonctl /usr/local/bin/
#COPY keeper-entrypoint.sh /usr/local/bin/
COPY pgpass.replication /etc/stolon/secrets/pgpass.replication
COPY pgpass.postgres /etc/stolon/secrets/pgpass.postgres

ENV STKEEPER_CLUSTER_NAME cluster01
ENV STKEEPER_DATA_DIR /keeper
ENV STKEEPER_LISTEN_ADDRESS 0.0.0.0
ENV STKEEPER_PORT 5431
ENV STKEEPER_STORE_BACKEND etcdv3
ENV STKEEPER_STORE_ENDPOINTS http://etcd:2379
ENV STKEEPER_PG_LISTEN_ADDRESS 0.0.0.0
ENV STKEEPER_PG_PORT 5432
#ENV STKEEPER_PG_BIN_PATH /opt/rh/rh-postgresql96/root/usr/bin/
ENV STKEEPER_PG_REPL_USERNAME replication
ENV STKEEPER_PG_REPL_PASSWORDFILE /etc/stolon/secrets/pgpass.replication
ENV STKEEPER_PG_SU_USERNAME postgres
ENV STKEEPER_PG_SU_PASSWORDFILE /etc/stolon/secrets/pgpass.postgres

RUN mkdir -p ${STKEEPER_DATA_DIR} && \
    chmod 700 ${STKEEPER_DATA_DIR} && \
    chmod 700 /etc/stolon/ && \
    chown postgres -R ${STKEEPER_DATA_DIR} && \
    chown postgres -R /etc/stolon/ 
USER postgres
EXPOSE 5432
#ENTRYPOINT ["keeper-entrypoint.sh"]

ENTRYPOINT /usr/local/bin/stolon-keeper --pg-listen-address=$HOSTNAME
