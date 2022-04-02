## Clase de Docker

Aplicacion en Node.JS, que tenga las siguientes funcionalidades:

- [X] Subir ficheros
- [X] Obtener ficheros subidos
- [X] Crear usuarios
    + Usuario/Password
- [ ] Autenticar usuarios
- [X] Asignar permisos a los ficheros subidos


S3, Simple Storage Service de Amazon
MinIO - Open Source

```bash
docker run -p 9002:9002 -p 9003:9003 -v $PWD/minio-data:/data \
  quay.io/minio/minio server /data --address=":9002" --console-address ":9003"
```

Lanzar postgres base de datos
```bash
docker run -d \
    --name some-postgres \
    -p 5436:5432 \
    -e POSTGRES_PASSWORD=postgres \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v $PWD/postgres-data:/var/lib/postgresql/data \
    postgres:14.2-alpine
```

Lanzar portainer, dashboard de docker
```bash
docker volume create portainer_data

docker run -d -p 8000:8000 -p 9900:9000 -p 9443:9443 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:2.9.3

```

## Desplegar aplicacion

- Construir un Dockerfile
- Construir la imagen Docker
- Subir la imagen Docker a un registro de contenedores (Docker Hub, quay.io, ghcr.io)
- Probar imagen docker en local
- Probar imagen docker en Kubernetes

Construir imagen:
```bash
docker build -t curso-nodejs:1.0.0 .
```

Lanzar imagen:
```bash
docker run --rm -p 3001:3000  --name curso-nodejs curso-nodejs:1.0.0 
```
