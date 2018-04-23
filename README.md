# docker-stolon-cluster

stolonctl --cluster-name cluster01 --store-endpoints http://etcd:2379 --store-backend etcdv3 status

vim /usr/lib/systemd/system/docker-compose.service

[Unit]
Description=docker-compose
Requires=docker.service
After=docker.service

[Service]
Restart=always
#WorkingDirectory=/opt/compose/

# Remove old containers, images and volumes
ExecStartPre=/usr/bin/docker-compose -f /opt/compose/docker-compose.yml down -v
#ExecStartPre=/usr/bin/docker-compose -f /opt/test.yml rm -v
#ExecStartPre=-/bin/bash -c 'docker volume rm $(docker volume ls -q)'
#ExecStartPre=-/bin/bash -c 'docker rmi $(docker images | grep "<none>" | awk \'{print $3}\')'
#ExecStartPre=-/bin/bash -c 'docker rm -v $(docker ps -aq)'

# Compose up
ExecStart=/usr/bin/docker-compose -f /opt/compose/docker-compose.yml up
#ExecStart=/usr/bin/docker-compose -f my.yml up

# Compose down, remove containers and volumes
ExecStop=/usr/bin/docker-compose -f /opt/compose/docker-compose.yml down -v
#ExecStop=/usr/bin/docker-compose -f my.yml down -v

[Install]