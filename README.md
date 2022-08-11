# FC-Serv-Discovery

## Iniciar docker-compose

docker-compose up -d

### Consultar 

docker-compose ps

## Subir o Server do Consul

docker exec -it <nome do server > sh

## Verificar os servers do consul

consul members

## Verificar IP da rede

ifconfig

usar o inet addr: xxx.xx.x.x

## Subir Server do Consul

consul agent -server -bootstrap-expect=3 -node=consulserver01 -bind=172.18.0.3 -data-dir=/var/lib/consul -config-dir=/etc/consul.d

consul agent -server -bootstrap-expect=3 -node=consulserver02 -bind=172.18.0.4 -data-dir=/var/lib/consul -config-dir=/etc/consul.d

consul agent -server -bootstrap-expect=3 -node=consulserver03 -bind=172.18.0.2 -data-dir=/var/lib/consul -config-dir=/etc/consul.d

## Unir dois servidores 

consul join xxx.xx.x.x

consul members -> deverá aparecer os dois servidores

## Subir client 

consul agent -bind=172.19.0.5 -data-dir=/var/lib/consul -config-dir=/etc/consul.d

## Subindo segundo client 

consul agent -bind=172.19.0.6 -data-dir=/var/lib/consul -config-dir=/etc/consul.d -retry-join=172.19.0.4 -retry-join=172.19.0.2

