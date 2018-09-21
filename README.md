https://docs.docker.com/get-started/

Intro
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

Service
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

Swarm
- SWARM is a group of machines (nodes) that are running Docker and joined into a cluster
