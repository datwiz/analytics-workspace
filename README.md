# Local Analytics Workspace
The Analytics Workspace provides a quick start environment for analytics work on a local desktop.  Services
provided in the workspace are Docker container based with data and config directories linked to the local
filesystem.

*WARNING:* This workspace is inteneded to be used in conjunction with Docker for Mac.  If this workspace is deployed
to a different Docker environment, such as a linux native environment, the security settings for the services
MUST be modified to enable security required when services are able to accessed from beyond the local host OS.

## Analytics Workspace Services
The following services are provided in the workspace:
* Jupyter notebooks, including Jupyter lab
* PostgreSQL database
* PGAdmin postgres SQL client and database admin tool

## Getting Started
1.  Make a copy of the analytics workspace project
```
# cd to the directory where the workplace will be created
git clone https://github.com/datwiz/analytics-workspace.git workspace
```

2.  Start the services
```
# cd into the workspace directory
cd workspace
# start the services
./bin/wsctl start
```

3.  Use the services
Access the services from your local browser.  Refer to [Accessing Services](#access) for details.

## About the workspace
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

## <a name="access" />Accessing Services
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

## Useful docker and docker-compose commands
### docker
### docker-compose
