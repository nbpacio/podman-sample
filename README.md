


#Connecting Containers via Podman:

## Create a Network:

```bash
podman network create pgnet
```

## Create Containers pointing to Network Created:

```bash
podman run -d --name my_postgres  --network pgnet  -e POSTGRES_DB=mydb  -e POSTGRES_USER=nbpacio       -e POSTGRES_PASSWORD=matrix21       -v postgres_data:/var/lib/postgresql       -p 5432:5432       docker.io/library/postgres:latest
```


```bash
podman run --name my_pgadmin4 --network pgnet -p 5050:80 -e PGADMIN_DEFAULT_EMAIL="nbpacio@gmail.com" -e PGADMIN_DEFAULT_PASSWORD="matrix21" -d docker.io/dpage/pgadmin4 
```


## Check IPs:

```bash

podman inspect <container> | grep -i networkmode
```

```bash
podman inspect <pod-name-or-id> | grep -i ip
```
