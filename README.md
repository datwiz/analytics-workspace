# Local Analytics Workspace
Provides a standard set of local services for an analytics workspace.

## Analytics Workspace Services
The following services are provided in the workspace:
* Jupyter notebooks, including Jupyter lab
* PostgreSQL database
* PGAdmin postgres SQL client and database admin tool

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
