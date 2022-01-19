# Docker, containers & images

## Images
Images are blueprints for docker containers. If you come from OOP background, it is the "Class" of sorts.

## Containers?
A container is an entire runtime environment: an application with all its dependencies, libraries, binaries, and configuration files needed to run it, bundled up into one package.

It is the running instance of a docker image. If you come from OOP background, it is the "Object" of sorts.

## Commands 
build 
```
docker build -t imageimage:version context

docker build -t thearyanahmed_docker_app:v1 .
```

## self explanatory commands 
```
// image
docker image ls
docker image rm thearyanahmed_docker_app:v1
docker rmi thearyanahmed_docker_app_image_id // deletes image by id

// containers 

// creating containers
docker create [options] IMAGE
  -a, --attach               # attach stdout/err
  -i, --interactive          # attach stdin (interactive)
  -t, --tty                  # pseudo-tty
      --name NAME            # name your image
  -p, --publish 5000:5000    # port map (host:container)
      --expose 5432          # expose a port to linked containers
  -P, --publish-all          # publish all ports
      --link container:alias # linking
  -v, --volume `pwd`:/app    # mount (absolute paths needed)
  -e, --env NAME=hello       # env vars

docker container ls
docker container rm -f $(docker ps -aq) // remove all containers (running and stopped)
// get container logs
docker logs $ID
docker logs $ID 2>&1 | less
docker logs -f $ID # Follow log output

docker container logs --tail 100 thearyanahmed_app_container

// running an app
docker container run --name $name -p $outter:$inner -e SOME_ENV_VARIABLE=VALUE -e ANOTHER_ENV=VALUE image:version
docker container run --name thearyanahmed_web_app -p 8000:8123 thearyanahmed/repote-repo-app:v5

// stopping a container using SIGTERM
docker container stop web 

// stopping a container using SIGKILL
docker container kill web 

// processes
docker ps 
docker ps -a // all 
docker kill $ID

// exec 
docker exec [options] CONTAINER COMMAND
  -d, --detach        # run in background
  -i, --interactive   # stdin
  -t, --tty           # interactive


docker exec app_web_1 tail logs/development.log
docker exec -t -i app_web_1 rails c


docker network ls
docker pull thearyanahmed_docker_app:1.0

//tagging 

docker tag localrepo:version username/repo:version
docker tag thearyanahmed_local_app:v3 thearyanahmed/hello-world:v4

// push 
docker push username/repo:version
docker push thearyanahmed/hello-world:v4


```