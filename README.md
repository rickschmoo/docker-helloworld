https://docs.docker.com/get-started/

1/2 Intro
- Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers
- A CONTAINER is launched by running an image. An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.
- DOCKERFILE defines what goes on in the environment inside your container
- `docker login`
- `docker build -t friendlyhello .`
- `docker run -d -p 4000:80 friendlyhello`
- `docker container stop XXX`
- `docker tag image username/repository:tag`
- `docker push username/repository:tag`
- `docker run -p 4000:80 username/repository:tag`

3 Service
- In a distributed application, different pieces of the app are called SERVICES.” = “containers in production.”
- Service runs one image
- defined with `docker-compose.yml`
- `docker swarm init`
- `docker stack deploy -c docker-compose.yml getstartedlab`
- `docker service ls`
- A single container running in a service is called a TASK
- List tasks: `docker service ps getstartedlab_web`
- `docker stack rm getstartedlab`
- `docker swarm leave --force`

4 Swarm
- SWARM is a group of machines (nodes) that are running Docker and joined into a CLUSTER. Multi-container, multi-machine applications are made possible by joining multiple machines into a “Dockerized” cluster called a SWARM
- swarm is made up of multiple nodes, which can be either physical or virtual machines
- commands executed on a cluster by a SWARM MANAGER
- other machines = WORKERS
- install Virtualbox
- `docker-machine create --driver virtualbox myvm1` (and myvm2)
- `docker-machine ls`
- `docker-machine ssh myvm1 "docker swarm init ...`
- `docker-machine ssh myvm2 "docker swarm join`
- `docker-machine ssh myvm1 "docker node ls"`
- `docker-machine env myvm1`
- `eval $(docker-machine env myvm1)`
- `docker stack deploy -c docker-compose.yml getstartedlab`
- `docker stack ps getstartedlab`
- Teardown: `docker stack rm getstartedlab`


5 Stacks
- A STACK is a group of interrelated services that share dependencies, and can be orchestrated and scaled together. stacks are inter-related services all running in concert
- add different images and container config to `docker-compose.yml`

Add visualiser
- `docker stack deploy -c docker-compose-step5a.yml getstartedlab`
- View <my vm1 ip>:8080
- `docker stack ps getstartedlab`

Add redis
- `docker-machine ssh myvm1 "mkdir ./data"`
- `docker stack deploy -c docker-compose-step5b.yml getstartedlab`
- `docker service ls`
- Access http://<my vm1 ip> and watch count from redis




