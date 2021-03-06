# Intro 2 Containerization & Shipping Software

### Agenda
* Homework Check
* Learning Conteinerization with Docker
* Homework

### Learning Conteinerization with Docker

##### Goals
Understand the benefits of conteinerizing processes and how to apply it using Docker. By the end of this class you will be able to:
* Understand what is conteinerization and why is it necessary
* Differentiate between images and containers
* Build new images
* Run and manage the conteiners lifecycle
* Create your own images and run them as containers
* Be able to navigate and use the Docker Hub to spin up production ready containers directly from it
* Conteinerize your final project so that it can be easily ran by any person on any environment

* [Getting Started with Docker](https://docs.docker.com/get-started/): Official Docker getting started page
* [Docker Workflow overview](https://docs.docker.com/engine/docker-overview/): Diagram showing lifecycle of images and containers
* [Docker Hub](https://hub.docker.com): Docker Hub with tons of images available
* [Docker Trend comparison](https://trends.google.com/trends/explore?date=today%205-y&geo=US&q=docker,big%20data,hadoop,machine%20learning): A trend chard comparing Docker to other important Big Data topics

##### Introducing conteinerization
* Conteinerization has been one of the most important software operations movement in the past 5 years
* Its main goal is to lower friction and costs in migrations that used to be extremely long and costly
  - Mainframes
  - Baremetal Datacenters
  - VMs
  - Cloud
  - Dev, Testing and Production environments
* It achieves it by making it transparent to the operator where the container is running because the process carries its own environment description with it
* There are short lived and long running Docker processes  

1. Check your `docker version`
2. Check your `docker info`
3. List all possible commands you can do with the docker client.
4. List your currently running containers, check for stopped ones too. It should be empty!
5. Run your first container! Run the official `hello-world` Docker Image. 
6. Read the text that shows up specially the 4 bullet points.
7. List your currently running containers again, check for stopped ones too.
8. Make sure to remove your stopped container.
9. Now start another `hello-world` container using the `--rm` flag. Do you need to remove it after?
10. Is `hello-world` a 'long running' process or a 'short lived' process?

##### Images VS Containers: Running Existing Images as Containers
* [Images and Containers](https://docs.docker.com/v17.09/engine/userguide/storagedriver/imagesandcontainers/): The anatomy of images and containers
* A Image is a blueprint that allows us to create multiple instances from it. Each instance is called a container.
* When running a container, we first check if the requested image is available locally. If not, docker searches for it in the specified repository or at DockerHub.
* Images can be seen as composable layers, and this is one of the biggest factors os success of Docker. Multiple different images can share layers, which saves a lot of space and decreases the load up time.
* Containers are an ephemeral layer created on top of the image layers just during it's own lifetime.

1. List all the images you have downloaded to your local machine.
2. List all the containers you have running or stopped on your local machine.
3. Open your browser and type localhost:80 in the url
4. Run the following image using the terminal:
* nginx (map the port 80:80 from the container)
5. Test the fact your webservers is up by checking the same url again. You should get a different page now.
6. List all the images you have downloaded to your local machine. Are there new images here?
7. Make sure to stop and remove your containers.
8. Cleanup your images to avoid consuming too much space now.

##### Creating your own Images and modifying existing Images
* [Dockerfile description](https://docker-curriculum.com/#dockerfile): Basics on writing a Dockerfile
* In order to create our own images we have to add a new file to our project: the `Dockerfile`. 

1. Write a small python script that only prints `I'm a short lived python script running within a docker container!!!`. Save it as `short-lived.py`
2. Create a new `Dockerfile` based on the ubuntu linux docker image. This image should always launch your `short-lived.py` script when started. You will need to make sure you install python3 in this image and also to copy your script to the containers.
3. Build this image and run it to test it.
4. Repeat the same steps, but now use a long running process. You can use a `while(True)` loop in  your python script in order to achieve this.
5. Make sure to cleanup by stopping and removing all containers.

##### Final notes on Docker
* ANY process can be Dockerized and the benefits are many:
  - This makes it not only repeatable but self documented, avoiding invalid documentation
  - All teams in company speak one language: containers
  - A process can have multiple Dockerfiles if necessary
* A few real life scenarios where Docker is used:
  - To write software that runs on different computer OS, datacenters, clouds
  - That don't require native libs compatibility
  - To testing apps in different environments at a low cost (OS, DBs, Hadoop, etc)
  - To facilitate CI/CD: automated testing suites, packaging, building and deployment to final environments
* You can find references for many Dockerfiles in the Official Images Docker Library, for example: [Python Docker Image](https://github.com/docker-library/python)

### Additional Exercises Material
* [Extra exercises](./4-docker-exercises.md): Additional exercises to practice each Docker topic

### Optional homework(no need to submit)
* Research what are `python functions`
* Research what are the `pandas` and `matplotlib` python libraries and what they're used for

### Recommended Readings
* [Docker Cheatsheet](https://github.com/wsargent/docker-cheat-sheet): All docker commands and cookbook recipes in a single place!
* [Official docker samples](https://docs.docker.com/samples/): Some Dockerfile samples
* [Official Images Dockerfiles](https://github.com/docker-library/): Images for the Official Docker Images
* [PySpark Jupyter image tutorial](https://medium.com/@suci/running-pyspark-on-jupyter-notebook-with-docker-602b18ac4494): how to run a PySpark Jupyter image in less than 3 minutes
* [What is Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/): What is Kubernetes, a high level architecture tool for container orchestration
