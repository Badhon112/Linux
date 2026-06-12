# Docker

- **What is a Container? How is it different from a VM?**
  - A Container is a light weight, stander execution software package that container every thing that need to run an application code.
  - Where a Vm is the OS rather then the physical hardware

- **Explain the Docker Architecture (Client, Host, Registry)**
  - Docker use a client-server architecture composed of 3 core component .
  - _Docker Client_ : The Client is the primary interface used to interact with Docker.
  - _Host_ : The host is actually the Physically machine or cloud machine where the application workload actually execute. It provides the complete environment to manage containers.
  - _Registry_ : The Registry is a centralizes, storage system repo holder and sharing containers images.

- **What is a Docker Image?**
  - A Docker image is a lightweight, standalone, and immutable (read-only) file that contains everything that needed to execute an application

- **Explain the layers in a Docker Image.**
  - The layer is a sequence of read-only layer, Where each layer that represent a set of filesystem changes (addition, deletions).

- **What is a Dockerfile?**
  - A Dockerfile is sequential script of instruction that is used to automatically assemble and build a Docker Image.

- **Explain the difference between ’CMD’ and ’ENTRYPOINT’.**
  - _CMD_ : CMD defines a default that can be overridden at runtime. Whereas ENTRYPOINT defines a fixed executable that always runs when the container starts

- **Difference between ’ADD’ and ’COPY’.**
  - Both ADD and COPY command used to transfer file from the host to the container
  - COPY for all local file transfer because it is straightforward and predictable. Where ADD Command is used to From an url or automatically extract local archives.

- **What is .dockerignore ?**
  - A .dockerignore file is a configuration text file used to specific which files and directory should be excluded/remove fom the docker build context

- **Explain Docker Networking (Bridge, Host, None).**
  - Docker network drivers control how container communicate with each other, the host machine and outside world.
  - _Bridge_ : The Bridge network is the standard driver automatically assigned to containers if you do not specific a network mode. "docker run -d --name web-app -p 8080:80 nginx"
  - _Host_ : The Host network completely removes network isolation between the container and your physical host machine. The container does not get its own ip address or network namespace. Instead. If as containerized application binds on port 80. It is instantly active on port 80 of your main physical server. "docker run -d --name high-perf-app --network host nginx" . It will only work on linux.
  - _None_ : The none network provides total network disconnection. The container is provisioned without any external network interface gateway , or routing configs. "docker run -d --name secure-job --network none alpine"
