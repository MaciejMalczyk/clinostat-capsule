# Docker image for storing images

This contains image with http and ssh server. In Dockerfile user "img" with password "img" is created as an entry point for sftp connections. Later each "cultivation" uses this to send ssh key. You can change this if you want.

This runs in net=host mode so ssh port in container is changed to 8022.

You can also change where images are stored. In compose.yaml this is set to dir inside user home folder, but you can use other dir or docker volume.

## Build:
```
docker build -t clinostate_images .
```

## Run:
```
docker compose up -d
```
