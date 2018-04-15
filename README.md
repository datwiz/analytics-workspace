# Local Analytics Workspace
Provides a standard set of local services for an analytics workspace.

## Analytics Workspace Services
The following services are provided in the workspace:
* Jupyter notebooks, including Jupyter lab
* PostgreSQL database
* PGAdmin postgres SQL client and database admin tool

## Environment and directories
### workspace root directory
The analytics workspace runs from a workspace root directory identified by the env var `WORKSPACE_ROOT_DIR`
`WORKSPACE_ROOT_DIR` can either be set explicitly or the defaults to the current working directory.

### directories
* postgresql database data `${WORKSPACE_ROOT_DIR}/data/postgresql/data`
* pgadmin config `${WORKSPACE_ROOT_DIR}/data/postgresql/pgadmin
* jupyter notebooks `${WORKSPACE_ROOT_DIR}/notebooks`

## Starting and Stopping Services
### starting services
`./bin/wsctl start`

### stoping services
`./bin/wsctl stop`
Note that the containers will be recreated again on start.

## Accessing Services
### Jupyter Notebook
```
http://localhost:8888/tree
```

### Jupyter Lab
```
http://localhost:8888/lab
```

### PostgreSQL
Database connections 
```
localhost:5432 from the desktopn
db:5432 from within the containers
username: <local_login>
password: password
```

### PGAdmin 4
```
http://localhost:8080
username: <local_login>
password: password
```

## Container Implementation
The workspace makes use of docker containers and docker-compose to manage and deliver workspace services.
The workspace is intended to be used in conjunction with *Docker for Mac*.  Docker for Mac restricts access
to the workspace services to the local environment, protecting services and data from external access.

*WARNING:* If this workspace is deployed to a different Docker environment, such as a linux native environment,
the security settings for the services MUST be modified to enable security required for secure external access.
