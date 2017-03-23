# Docker #

## Standard Commands ##

#### Build Current ####
`docker build -t <image_name> .`

#### List Local Images ####
`docker images`

#### Run Image ####
`docker run --name <instance_name> --link <required service> --env-file ./.env.list -i -t -p 1337 <image_name>`

## Troubleshooting ##

#### Cannot connect to the Docker daemon. Is the docker daemon running on this host? ####
run `eval "$(docker-machine env default)"`
