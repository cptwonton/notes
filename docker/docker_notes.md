`docker --version`
`docker info`

## run a docker image
`docker run hello-world`

`docker image ls`

`docker container ls`
`docker container ls --all`

`docker run -d -p <machine port>:<container port> <container friendly name>`
-d for detached (running in background)

`docker container stop <containerID>`
containerID comes from `docker container ls`
