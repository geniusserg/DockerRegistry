# docker-registry

## How to setup

### Local registry with UI

docker network create registry-ui-net
docker run -d --net registry-ui-net --name registry-srv registry:2
docker run -d --net registry-ui-net -p 80:80 -e REGISTRY_URL=http://registry-srv:5000 -e DELETE_IMAGES=true -e REGISTRY_TITLE="My registry" joxit/docker-registry-ui:static

### Authentication
apt install apache2-utils

htpasswd -c password admin (To add new user remove -c flag)

cp password nginx/auth

### Get SSL Certificate
[SSLforFree](http://sslforfree.com)

cat sertificate.crt ca_bundle.crt > server.crt

cp private.key certs

cp server.crt certs

### Launch
> docker-compose up

### Open in browser
https://<host> (admin/admin)


