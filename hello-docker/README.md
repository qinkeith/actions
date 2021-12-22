# GitHub docker action

## Add a `Dockerfile`

```
# Container image that runs your code
FROM alpine:latest

# Copies your code file from your action repository, like qinkeith/hello-docker-action, to the filesystem path `/` of the container
COPY entrypoint.sh /entrypoint.sh

# Runs the command to add the execute permission to the entrypoint.sh
RUN chmod +x entrypoint.sh

# Code file to execute when the Docker container starts up
ENTRYPOINT ["/entrypoint.sh"]
```

## Create a metadata file called `action.yml`

```
name: "Hello Docker action"
description: 'Simply running a bash command and showing the time it executed'
runs:
 using: "docker"
 image: "Dockerfile"
```

## Implement the action logic in a bash file `entrypoint.sh`

```
#!/bin/sh -l
echo "Hello $GITHUB_ACTOR! The time now is $(date)"
```
