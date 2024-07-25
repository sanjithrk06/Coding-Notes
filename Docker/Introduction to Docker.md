Documentation : https://docs.docker.com/
Docker Desktop Installation : https://docs.docker.com/desktop/install/windows-install/
Next Topic : 


## **What is Containers**

- Imagine a team is developing a web application with some components like node, python , sql etc.. 
- If a new developer is joining the team. He has to install the node , python, sql to continue on this project.
- If he install all the necessity, he don't know that whether the version is same as other developer's version.
- Here comes the containers.
- Containers are isolated processes for each of your app's components. (i.e. node, python, sql - runs in it's own isolated environment) Completely isolated from everything else on your machine.
- Containers are : 
	1. Self-contained
	2. Isolated
	3. Independent
	4. Portable
#### Containers vs VMs
- a VM is an entire operating system with its own kernel, hardware...  Running a VM only to isolate a single application is a lot of overhead.
- But a container is simply an isolated process with all of the files it needs to run. If you run multiple containers, they all share the same kernel, allowing you to run more applications on less infrastructure.

## **What is Images**

- Containers use images to share the files and configurations.
- A container image is a standardized package that includes all of the files, binaries, libraries and configurations to run a container.
-  Two important principles of images:
	1. Images are immutable. Once a image is created, it can't be modified. You can only make a new image or add changes on top of it.
	2. Container images are composed of layers. Each layer represented a set of file system changes that add, remove, or modify files.

#### Where do you store these images?

- You can store the image in your system but if you want to share it with your friends or use it on another machine?
- So that Container images will be stored in image registry which is a centralized location for storing and sharing your container images.
- It can be either public or private. Docker Hub is also a public registry that anyone can use and is the default registry.
- And there are many other available container registers available including [Amazon Elastic Container Registry(ECR)](https://aws.amazon.com/ecr/), [Azure Container Registry (ACR)](https://azure.microsoft.com/en-in/products/container-registry), and [Google Container Registry (GCR)](https://cloud.google.com/artifact-registry).
- You can even run your private registry on your local system or inside your organization. For example, Harbor, JFrog Artifactory, GitLab Container registry etc.
	![[Pasted image 20240725142821.png|300]]

## What is Docker Compose?

- You're wanting to do something more complicated - run databases, message queues, caches, or a variety of other services.
- You can use docker compose, it will run multiple containers.
- With docker compose, you can define all of your containers and their configurations in a single YAML file.
- For every time you makes changes to the compose file, you need to run `docker compose up`.

#### Docker file vs Compose file

A Docker file provides instructions to build a container image while a Compose file defines your running containers. Quite often, a Compose file references a Docker file to build an image to use for a particular service.