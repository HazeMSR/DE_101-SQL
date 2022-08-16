# Data Engineering 101 - SQL

This repository will be hosting the current directories of the databases containers.

## Docker
Docker provides virtual infrastructure to deploy any type of services.

The Docker part use two files:
1. .env.dev: This file is used to contain the environment variables (In this case for the development enviroment)
2. docker-compose.yml: This file contain the docker services description in order to build the containers.

### Docker commands
```bash
# Start (and create if it is neccesary) the services described in the yaml file
docker-compose up
# OPTIONS:
# --env-file [file] Take an environment file to use the variables as an input for docker-compose.yml
# -d Detach mode: Start services in the foreground.

# Execute commands to run inside the container
docker exec container-name command-to-execute
# OPTIONS:
# -i Interactive mode: Keep STDIN open even if not attached
# -t Allocate a pseudo-TTY: is essentially a text input output environment aka shell.
# container-name: Specify the container name or ID
# command-to-execute: The most common command is /bin/bash, maybe you must use /bin/sh instead (You can use psql or mysql commands here)

# Show the current running docker services
docker ps
# Recommendation:
# Run with | grep your_container_name in order to watch only your desired containers

# Stop a container
docker stop container_name

# Delete a container
docker rm container_name

# Delete an image
docker rmi image_name

# Stops all the services of the docker-compose file
docker-compose stop
```

### MySQL commands
```bash
# Run MySQL shell in the specified database
mysql db_name
# OPTIONS:
# -h [host_name] Indicates the url of the database
# -p Indicates to use the prompt to use it as a input of the password
# -u [user_name] Indicates the username who will be used to connect to the database
# -e [command] Execute some MySQL command inside.

# Dump a complete database and/or their procedures
mysqldump dbname > filename.sql
# OPTIONS:
# --routines Export all the routines (Procedures/Functions) of the database inside the dump file
# --triggers Export all the triggers of the database
# --add-drop-table Add the "drop table if exists" sentence on every table
# -p Indicates to use the prompt to use it as a input of the password
# -u [user_name] Indicates the username who will be used to connect to the database

```

## Indexes

```sql
# Hash index
CREATE INDEX "my_table_my_column_idx"
ON "my_table"
USING HASH("my column");

# B-tree composite index
CREATE INDEX "my_table_my_columns_idx"
ON "my_table" ("my column1", "my_column2", "my_columnN")
```
