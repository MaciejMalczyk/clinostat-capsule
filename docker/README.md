# Docker image for storing images

Contains an image with an HTTP and SSH server. In the Dockerfile, a user "img" with password "img" is created as an entry point for sftp connections. Later, each "cultivation" uses this to send an SSH key. You can change this if you want.

Runs in net=host mode, so the SSH port in the container is 8022.

You can also change where images are stored. The default is the directory in the home folder. Any other directory or Docker volume is valid. You can set it in compose.yaml.

## Build:
```
Docker build -t clinostate_images.
```

## Run:
```
docker compose up -d
```
