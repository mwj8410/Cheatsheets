# Docker #

## Standard Commands ##

#### Build Current ####
`docker build -t <image_name> .`

#### List Local Images ####
`docker images`

#### Clean Local Images ####
```bash
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
```

#### Clean Network ####
Often encountered with testing or frequently failing images
`docker network prune`

#### Run Image ####
`docker run --name <instance_name> --link <required service> --env-file ./.env.list -i -t -p 1337 <image_name>`

## Troubleshooting ##

#### Cannot connect to the Docker daemon. Is the docker daemon running on this host? ####
run `eval "$(docker-machine env default)"`

#### Kill all containers ####
`docker rm -f $(docker ps -a -q)`
