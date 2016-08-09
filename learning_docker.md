#Learning docker

> Docker images can be taken from docker hub. Docker is currently not supported in windows. Docker installed machine is called a Docker host. By default docker does not listen on any port. Changes have to done to listen on a port in config file **/etc/default/docker**  as `DOCKER_OPTS="-H tcp://0.0.0.0:4332 -H unix:///var/run/docker.sock"` and restart the docker services . This will make the docker listen on port 4332. 

* `docker ps` -- Will show the running docker containers in a docker host
* `docker ps -a` -- Will list all the docker containers that are in running,stopped condition
* `docker images` -- Will list all the images in a docker host
> Docker images are available in docker hub. Images can be created locally as well
* `docker history '<image name>'` -- Will give the details on the image built history
* `docker inspect '<image name>'` -- To inspect the image with meta data
* `docker pull <image name>` -- Will pull the mentioned docker image from docker hub if available
* `docker run -i -t <image name>` -- Will run the docker in interactive mode and assign a tty
* `docker run -d <image name>` -- Will run the docker container as daemon
* `docker run -d --name='<dockername>'` -- Will run the docker container as daemon and give a name to it 
* `docker run -d --name='<dockername>' -p <host port>:<containerport>` -- Will map the docker container port to port on docker host
* `docker run -d --name='<dockername>' -P ` -- Will assign any random port on the docker host corresponding the docker container port
* `docker exec -it '<docker container>' '<command>'` -- To execute a command on running container
* `docker attach '<docker container>'` -- To attach to a running container 
* `docker diff '<docker container>'` -- Will give changes done on a container after running it
* `docker top '<docker container>'` -- Will give utilization of running container
* `docker log -f <docker container>'` -- Will give the logs on docker container
* `docker run -d -v '<path on docker host>':'<path on docker container>'` -- Volumes on the docker container can be mapped with option v
* `docker run -d -p 80:80 -v /opt/postgres/date:/var/lib/postgresql/data -e POSTGRES_PASSWORD=postgres` -- Environment variables can be set by opetion e when running a docker container.Variables present in a docker image can be found using inspect option