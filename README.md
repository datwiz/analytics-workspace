# Local Analytics Workspace
The Analytics Workspace provides a quick start environment for analytics work on a local desktop.  Services
provided in the workspace are Docker container based with data and config directories linked to the local
filesystem.

*WARNING:* This workspace is intended to be used in conjunction with *Docker for Mac*.  If this workspace is deployed
to a different Docker environment, such as a linux native environment, the security settings MUST be modified to enable
security required when services are able to accessed from beyond the local host OS.

## Analytics Workspace Services
The following services are provided in the workspace:
* Jupyter notebooks, including Jupyter lab
* PostgreSQL database
* PGAdmin postgres SQL client and database admin tool

## Getting Started
1.  Make a copy of the analytics workspace project\
Open a terminal window and change to the directory where the workspace is to be created.
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

3.  Use the services\
Refer to [Accessing Services](#access) for details on accessing the services.

## About the workspace
### directories
* `${WORKSPACE_ROOT_DIR}/data/postgresql/data`     postgresql database data
* `${WORKSPACE_ROOT_DIR}/data/postgresql/pgadmin`  pgadmin config and session data
* `${WORKSPACE_ROOT_DIR}/notebooks`                jupyter notebooks and lab config and notebook data

### docker images
The docker images are pegged to the version tags current as of 16-Apr-18.  To use different docker
images, modify the `docker-compose.yml` file and change the tags to the desired versions.

### starting and stopping services
The `wsctl` utility manages the services in the workspace.

#### starting services
`./bin/wsctl start`\
Starts the container services.  If the services are already running, then the status is displayed.

#### stoping services
`./bin/wsctl stop`\
Stops the services.  The service containers remain and can be started again.

#### restarting services
`./bin/wsctl restart`\
Stops the services, if running, and starts the services again.

#### reseting services
`./bin/wsctl reset`\
Stops the services and removes the containers.  Note that new containers will be recreated again on start.

#### check service status
`./bin/wsctl status`\
Provides the runtime status of the workspace services.

## <a name="access" />Accessing Services
The services are configured to startup using the local username to run and access services.\
Running `whoami` in the terminal can be used to check the local username. 

As the services are only available from the localhost, simple default values for access passwords are used.
Different username / password credentials can be set by editing the `docker-compose.yml` file.

### Jupyter Notebook
The classical Jupyter notebook.
```
http://localhost:8888/tree
```

### Jupyter Lab
The new Jupyter lab.
```
http://localhost:8888/lab
```

### PostgreSQL
Database access, e.g. for use with JDBC or ODBC connections.
```
localhost:5432 from the desktopn
db:5432 from within the containers
username: <local_login>
password: password
```

### PGAdmin 4
Admin and SQL client
```
http://localhost:8080
username: <local_login>
password: password
```
