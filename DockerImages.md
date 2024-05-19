# Why do we need images?

Before now when bare metal was the de facto standard for IT infrastructure, each physical server was dedicated to running a single operating system and application stack, leading to inefficiencies in resource utilization and scalability. With the advent of virtualization, virtual machines enabled the abstraction of hardware resources and introduced more flexibility and efficient resource allocation. Containers introduced a game-charger perspective; offering lightweight and isolated execution environments that contain only application codes and their dependencies.

Docker images signify the entire environment needed for an application to run, including the operating system, dependencies, and other configurations. This makes applications to be able to run efficiently across environments, e.g. development, testing, and production. Images are built from Dockerfiles which are read-only templates containing instructions for creating a container. A Dockerfile is the blueprint for an image and an image in turn is run to create a container.

Here are some other characteristics of docker images:

- Immutable: Once built, Docker images are immutable, meaning their contents cannot be altered or modified. This ensures consistency and reproducibility across different environments.

- Layered: Docker images are composed of multiple layers, with each layer representing a filesystem snapshot. This layered approach enables efficient sharing and reusability of common components among different images.

- Tagged: Each Docker image can have multiple tags, which serve as unique identifiers for different versions or variants of the image. Tags allow for versioning and tracking of image changes over time.

- Portable: Docker images are highly portable, enabling applications and their dependencies to be packaged into self-contained units that can run consistently across different environments and platforms.

- Efficient: Docker images are designed to be lightweight and efficient, minimizing resource consumption and maximizing performance. This efficiency enables faster deployment times and improved resource utilization.

- Composable: Docker images can be composed or layered together to build more complex applications or services. This composability allows for code reuse and modularity in application development.

- Scalable: Docker images facilitate horizontal scalability by enabling applications to be deployed and replicated across multiple containers or container instances. This scalability enables organizations to meet fluctuating demand and scale resources dynamically.

- Secure: Docker images can be scanned for vulnerabilities and compliance issues, helping to identify and mitigate security risks early in the development lifecycle. Additionally, Docker provides built-in security features to enhance the isolation and security of containerized applications.

- Versioned: Docker images can be versioned using tags, allowing developers to track changes and manage different versions of their application code and dependencies. This supports efficient collaboration, testing, and rollback strategies.

- Managed: Docker images can be managed and distributed using container registries, providing centralized repositories for storing, versioning, and sharing Docker images. Container registries enable efficient image distribution and deployment workflows.


## What do images contain?

An image is made of sequential layers that cause a change in the container environment and make up an application. Images contain the code or binary, runtimes, dependencies, and other filesystem objects to run an application. The image relies on the host operating system (OS) kernel.

A container’s initial state can be whatever the developer wants — it might have an installed and configured web server or nothing but a bash shell running as root. In practice, though, most images include some preconfigured software and configuration files.

For example, to build a web server image, you can follow either of these approaches:

APPROACH 1
----------------

1. Start with an image for a Linux OS such as Ubuntu 20.04 (a base OS).
2. Add packages like Apache2 or Nginx.
3. Configure the web server and deploy the application as needed.

APPROACH 2
----------------

1. Fetch an official or custom web server image of your choice from a remote repository.
2. Configure the webserver and deploy the application as needed.

## Searching images

Searching for Docker images is a crucial step in the containerization process, enabling developers to find pre-built images that meet their application requirements. By utilizing Docker's vast repository of images available on platforms like Docker Hub or private registries, developers can leverage existing solutions and accelerate their development workflows. Through keyword-based searches and filtering options, developers can efficiently discover, evaluate, and pull Docker images tailored to their specific use cases, promoting productivity and collaboration within their teams.

### Search for images using the CLI

The default image repository/registry for docker is [Docker Hub](https://hub.docker.com/).

Search for Docker images on Docker Hub using the `docker search` command followed by a specified `<image name>`. 

You are just getting started with containerization and you learnt that there is tool called Portainer that can help you manage your container workloads using a Graphical User Interface. Now you have decided to search Docker Hub for it.

You can search for all `Portainer` images:

```bash
docker search portainer
```

You polled Docker Hub and got a list of available Portainer images:

```txt
NAME                                  DESCRIPTION                                     STARS     OFFICIAL
portainer/portainer                   This Repo is now deprecated, use portainer/p…   2517      
portainer/portainer-ce                Portainer CE - a lightweight service deliver…   2252      
portainer/agent                       An agent used to manage all the resources in…   235       
portainer/portainer-ee                Portainer BE - a fully featured service deli…   110       
portainer/portainer-k8s-beta          Portainer for Kubernetes BETA                   5         
portainer/compose-unpacker            A tool used to deploy Compose stacks from Gi…   1         
portainer/agent-k8s-beta              Portainer for Kubernetes BETA (agent)           1         
portainer/portainer-updater           A tool used to automatically update Portaine…   1         
portainer/template-swarm-monitoring   Repository containing the images used by the…   0         
portainer/helper-reset-password                                                       6         
portainer/base                        Multi-stage build image to create the Portai…   4         
portainer/kubectl-shell                                                               1         
portainer/golang-builder              Utility to build Golang binaries.               8         
portainer/kube-tools                  Image including Docker, kubectl and kind        1         
portainer/k2d                         Kubernetes to Docker translator                 0         
portainer/portable-env                                                                0         
portainer/angular-builder             Builder image for Portainer frontend.           1         
portainer/portainer-extension                                                         0         
portainer/dev-toolkit                 The entire Portainer development stack insid…   5         
portainer/pause                       pause container built by the official Kubern…   0         
portainer/helper-templates            A container helper for template file operati…   0         
portainer/docbuilder                  Portainer.io documentation builder              1         
portainer/pri-fidoiot                 Docker images for the FIDO Device Onboard (F…   0         
portainer/authenticator               Helps you use the Docker CLI with the Portai…   1
```

The returned list of images is categorized based on these parameters:

- Name: Represents the name of the Docker image in the search results.
- Description: Provides a brief description or summary of the Docker image, detailing its purpose or functionality.
- Stars: Indicates the number of stars or popularity ratings given to the Docker image by users, reflecting its popularity or quality.
- Official: Specifies whether the Docker image is an official image maintained by Docker or its affiliated organizations.

Here is basic syntax for searching docker images:

```bash
docker search <image name>
```

### Search for images on a Docker Image Registry

Docker registries such as [Docker Hub](https://hub.docker.com/) serve as centralized repositories for Docker images, offering version control, access management, and scalability. They streamline the process of distributing container images across different environments and teams, facilitating collaboration and ensuring consistency in deployments.

Navigating Docker Hub's user-friendly interface provides developers with effortless access to a wealth of Docker images, offering a seamless experience compared to command-line interfaces. With its intuitive search functionality and well-organized categories, developers can efficiently explore and discover pre-built images tailored to their specific requirements. Interacting with Docker Hub is simplified through its straightforward interface, allowing users to effortlessly browse, evaluate, and pull Docker images, facilitating rapid development and deployment workflows.

In order to search for available Nginx images on the Docker hub website, you can:

1. Navigate to the Docker Hub website: https://hub.docker.com/.

2. Type "Portainer" into the search bar located at the top of the page to search for Nginx Docker images.

3. Notice that official images have the "Docker Official Image" badge on them.

4. Utilize different filters, such as OS architecture, popularity, or version, to refine your search further and find the most suitable Portainer image.

5. Click on a desired image e.g [portainer-ce](https://hub.docker.com/r/portainer/portainer-ce) to access its dedicated page.

6. See a detailed description showing what the image is, how to run it, the image variants, licenses, how to pull the image, and other information.

6. Explore the specific tags of an image by clicking on the "Tags" tab to explore all the available tags associated with the image.

7. Delve deeper into specific tags by simply clicking on any tag to unveil additional details and information like the base image and the layers that the image contains.

## Pulling images from a Docker Image Registry

After searching for images and identifying the image that meets your needs. The next step is to retrieve the image to your local development environment. Fetching an image from a docker image registry such as Docker Hub is referred to as "pulling" the image.

Follow these steps to pull the Portainer (community edition) image:

1. Log on to Docker Hub

To interact with Docker Hub, users need to authenticate by logging in using their Docker Hub credentials. This ensures secure access to Docker Hub's features, such as pulling and pushing images.

> Note: This step is optional if you are just pulling images. You can pull an image without necessarily logging in to Docker Hub.

Login to your Docker Hub repository:

```bash
docker login
```

You logged in to Docker Hub and can now push images to your repository.

> Upon executing this command, you'll be prompted to enter your Docker Hub username and password.

2. Pull an image

Fetch an image to your local environment:

```bash
docker pull portainer/portainer-ce:latest
```

In this example, you use the `docker pull` command, including the username, image name, and tag or version. Here's the basic syntax:

```bash
docker pull username/image_name:tag
```

The tag or version after the colon is optional. 

## Listing images

List all the images on your local environment:

```bash
docker images

docker image ls
```

In this example, you used the `docker images` or `docker image ls` command to list images on your local machine.

Here is a sample output:

```
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
sample              latest    15efa209f8a2   6 days ago      750MB
hello-world         latest    ee301c921b8a   10 months ago   9.14kB
portainer/portainer latest    9281e1907542   17 months ago   278MB
```

What if you don't want to list all images and properties?

You can list only the image IDs: 

```bash
docker images -q
```

The `-q` flag used with the `docker images` command helps you to list only the image IDs.

You can list only the image names: 

```bash
docker images --format "{{.Repository}}"
```

The `--format "{{.Repository}}"` flag used with the `docker images` command helps you to list only the image names.

You can list only images that contain a particular tag: 

```bash
docker images portainer/portainer-ce
```

This examples helps you to focus on just a particular image tag of interest, in this case the `ubuntu` tag.

Being able to just list only the needed image properties helps you focus on exactly what you need.

## Understanding image tags

Image tags are used to label different versions or variants of an image. Developers use tags to manage and reference different versions of an image within a repository. Image tags are appended to the image name with a colon (:) separator. For example, `portainer/portainer-ce:latest` or `portainer/portainer-ce:2.20.2`. You can also tag an image `latest` which specifies that it is the most recent version of that image. If no tag is specified when pulling an image, Docker will pull the latest image. For example, running `docker pull portainer/portainer-ce` will pull the latest version of the portainer-ce image. 

An image tag is usually written using semantic versioning. An example is using the `major.minor.patch` pattern. For example, an image with the tag `portainer/portainer-ce:2.20.2` suggests that the major version is `2`, the minor version is `20` and the patch version is `2`.

Some images may have aliases for specific versions. For example, an image tagged `ubuntu:20.04` might also have an alias `ubuntu:focal`.

Images can also be tagged based on whether they are stable releases or development versions. For example, the `nginx:stable` image is for stable releases, and the `nginx:mainline` image is for development versions. 

An image can also have multiple tags which allows the image to be referenced interchangeably using any of the associated tags.

## Understanding image sizing

When selecting a docker image for use, it is important to consider sizing. Note that the size of an image can determine the container workload and performance and you should decide on the appropriate size of image to use according to your use case. 

You just learnt about a new database (SurrealDB) and you want to play around with it. You have decided to pull the image but you are trying to choose the lightest image possible.

First, confirm the repository name for this new database:

```bash
docker search surrealdb
```

The output shows that the repository name is `surrealdb/surrealdb`

To make your search for the different tags of `surrealdb/surrealdb` easier, install [Skopeo](https://github.com/containers/skopeo/blob/main/install.md/). 

For instance, if you are a Mac OS user:

```bash
brew install skopeo
```

Use `Skopeo` to search for different tags available for `surrealdb/surrealdb`:

```bash
skopeo list-tags docker://docker.io/surrealdb/surrealdb
```

Here is a sample output:

```json
{
    [
        ...
        "v1.3.1-dev",
        "v1.4.0",
        "v1.4.0-beta.1",
        "v1.4.0-beta.1-dev",
        "v1.4.0-dev",
        "v1.4.2",
        "v1.4.2-dev",
        "v1.5.0-beta.1",
        "v1.5.0-beta.1-dev"
    ]
}
```

Pull and confirm the size for the tags of choice e.g `v1.4.2` and and `v1.4.2-dev`:

```bash
docker pull surrealdb/surrealdb:v1.4.2
docker pull surrealdb/surrealdb:v1.4.2-dev
docker images surrealdb/surrealdb
```

The output shows that the sizes of the dev and regular `v1.4.2` versions are `115MB` and `43.5MB` respectively. Repeat the steps to choose the best image that suits your sizing requirements.

# Building your own images

## Introduction to Dockerfile

In order to build an image, you need a Dockerfile. Dockerfiles are text files that contain a set of instructions for building an image. In a Dockerfile, you can define the environment and configurations needed to run an application. Using Dockerfile for defining the image helps keep the image definition consistent. The image definition can be checked out to a version control system and any member of a development team can use that to replicate exactly the same image.

Each instruction in a Dockerfile represents a step in the image-building process. The instructions are in essence commands to specify the base image to use, to install dependencies, to copy files, to set environment variables, amongst other things.

### The basic template for a Dockerfile

A Dockerfile usually starts by referencing a base image that you would like to use. The Dockerfile that you will end up with depends on the kind of custom image that you would like to create. Let's assume that you want an image with Nginx installed, you can have different Dockerfiles achieving this differently.

Here is a `Dockerfile` that uses an official `Nginx` base image to package a sample Flask application (https://github.com/realpython/flask-by-example/):

```Dockerfile
# Use an Nginx image as the base
FROM nginx:1.21.3

# Set the working directory to /usr/share/nginx/html
WORKDIR /usr/share/nginx/html

# Install dependencies
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    build-essential \
    python3 \
    python3-pip \
    libpq-dev

# Download and install a Python application from GitHub
RUN wget https://github.com/realpython/flask-by-example/archive/refs/heads/master.zip && \
    unzip master.zip && \
    mv flask-by-example-master/* . && \
    rm -rf flask-by-example-master master.zip

# Install Python dependencies
RUN pip3 install -r requirements.txt

# Set initial environment variables to get the application running
ENV APP_SETTINGS="config.DevelopmentConfig"
ENV DATABASE_URL="postgresql:///wordcount_dev"

# Install Gunicorn
RUN pip3 install gunicorn

# Create the Nginx configuration file to serve the application
RUN echo "user www-data;\n\
worker_processes auto;\n\
pid /run/nginx.pid;\n\
include /etc/nginx/modules-enabled/*.conf;\n\
events {\n\
    worker_connections 768;\n\
}\n\
http {\n\
    sendfile on;\n\
    tcp_nopush on;\n\
    tcp_nodelay on;\n\
    keepalive_timeout 65;\n\
    types_hash_max_size 2048;\n\
    include /etc/nginx/mime.types;\n\
    default_type application/octet-stream;\n\
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;\n\
    ssl_prefer_server_ciphers on;\n\
    access_log /var/log/nginx/access.log;\n\
    error_log /var/log/nginx/error.log;\n\
    gzip on;\n\
    include /etc/nginx/conf.d/*.conf;\n\
    include /etc/nginx/sites-enabled/*;\n\
    server {\n\
        listen 80;\n\
        location / {\n\
            proxy_pass http://127.0.0.1:8000;\n\
            proxy_set_header Host \$host;\n\
            proxy_set_header X-Real-IP \$remote_addr;\n\
        }\n\
    }\n\
}" > /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start Gunicorn and Nginx when the container launches
CMD ["sh", "-c", "service nginx start && gunicorn -b 0.0.0.0:8000 app:app"]
```

Here is an another `Dockerfile` that uses `python:3.7-slim` as a base image instead:

```Dockerfile
# Use Python 3.7 slim as the base image
FROM python:3.7-slim

# Set the working directory to /app
WORKDIR /app

# Install dependencies
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    build-essential \
    libpq-dev

# Download and install a Python application from GitHub
RUN wget https://github.com/realpython/flask-by-example/archive/refs/heads/master.zip && \
    unzip master.zip && \
    mv flask-by-example-master/* . && \
    rm -rf flask-by-example-master master.zip

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Set initial environment variables to get the application running
ENV APP_SETTINGS="config.DevelopmentConfig"
ENV DATABASE_URL="postgresql:///wordcount_dev"

# Install Gunicorn
RUN pip install gunicorn

# Expose port 8000
EXPOSE 8000

# Start Gunicorn when the container launches
CMD ["gunicorn", "-b", "0.0.0.0:8000", "app:app"]
```

Try to build the image and spin up the container.

### Common instructions in a Dockerile

Now that you have a feel of what a Dockerfile looks like, let's look at the common Dockerfile instructions. Here are some of the most important ones.

- FROM
- RUN 
- COPY
- EXPOSE
- CMD

Others include:

- WORKDIR
- CMD
- ENTRYPOINT

These instructions are pretty much all you need to containerize your application. However, check out the documentation at https://docs.docker.com/reference/dockerfile/ to explore more Dockerfile instructions.

#### FROM

Use the `FROM` instruction to specify the base image to use for the new custom image that you are building. The `FROM` statement is very important because it is the starting point of an image definition. Every image should ideally have a base image and the `FROM` instruction helps us to define a filesystem/operating system layer for the custom image.

For example, you can specify that the Dockerfile should start off using the `ubuntu:20.04` as the base image using the `FROM` instruction:

```dockerfile
FROM ubuntu:20.04
```

Here is the basic syntax:

```Dockerfile
FROM <image>[:<tag>] [AS <name>]
```

- `<image>`: This is used to specify the base image of choice. The base image can be an image on your local machine, an image in a public container image repository, or a private registry.
- `<tag>`: This is an optional parameter that helps us specify the version or tag of the base image. The latest image is used by default if you don't specify a tag.
- `<name>`: This is an optional parameter that is used to assign an alias to the base image which can be referenced later on for example in a multi-stage build.

#### WORKDIR

Use the `WORKDIR` instruction to set the working directory where actions will be performed. Subsequent commands like `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` usually follow the `WORKDIR` instruction.

For example, you can use the `WORKDIR` instruction to set the working directory inside the container to `/app`:

```dockerfile
FROM ubuntu:20.04
WORKDIR /app
```

Here is the basic syntax:

```Dockerfile
WORKDIR /path/to/directory
```

- `/path/to/directory`: This parameter is used to specify the path inside the container where subsequent commands will be executed. The directory specified will be created if it does not exist and as such the `WORKDIR /path/to/directory` is a smarter alternative to `RUN mkdir -p /path/to/directory`.

All subsequent commands/instructions in the Dockerfile will be executed in the given path unless another `WORKDIR` instruction is specified down the line. 

You can create two files at different paths within the container:

```Dockerfile
FROM ubuntu:20.04
WORKDIR /app
RUN echo "Learning about Docker" > file1.txt

WORKDIR /app/tmp
RUN echo "Learning about containers" > file2.txt
```

In this example, you use the `WORKDIR` instruction to set context and determine the target path for the subsequent `RUN` instruction. The first `RUN` instruction will be executed inside the `/app` directory while the second `RUN` instruction will be executed in the `/app/tmp` directory. This suggests that the absolute paths of the two files will be `/app/file1.txt` and `/app/tmp/file2.txt` respectively.

#### COPY

Use the `COPY` instruction to copy files or directories from the build context (the directory on the host machine where the `docker build` command is being executed) into the container filesystem.

For example, you can use the `COPY` instruction to replace the Nginx configuration file inside the container by copying a custom `nginx.conf` file in the build context to the `/etc/nginx/nginx.conf` inside the container:

```dockerfile
FROM nginx:1.25.4

# Copy custom nginx configuration file
COPY nginx.conf /etc/nginx/nginx.conf
```

Here is the basic syntax:

```Dockerfile
COPY <src> <dest>
```

- `<src>`: This is used to specify the path to the file or directory on the host machine relative to the build context.
- `<dest>`: This is used to specify the destination path inside the container where the file or directory will be copied.

#### ADD

Use the `ADD` instruction to manipulate files and directories during the image build process. While similar to `COPY`, ADD comes with additional functionalities like extracting compressed files and retrieving files from URLs.

For example, you can use the `ADD` instruction to add a copy of a local file `app.py` into the `/app` directory within the container. You can also fetch an archive from a URL `https://website.com/archive.tar.gz` and unpack it into the `/data/` directory within the container:

```Dockerfile
FROM alpine:3.14

ADD app.py /app/

ADD https://website.com/archive.tar.gz /data/
```

Here is the basic syntax:

```Dockerfile
ADD <src> <dest>
```

- `<src>`: This is used to specify the path to the file or directory on the host machine relative to the build context. It can be a URL or an archive
- `<dest>`: This is used to indicate the destination path inside the container where the file or directory will be added.

#### RUN

Use the `RUN` instruction to execute commands inside the container when the image is built. This allows us to install application dependencies, run scripts, or configure the environment as required.

For example, you can use the `RUN` instruction to run three commands which will update the package index, install the Nginx package, and clear out the local repository of the Nginx package:

```dockerfile
FROM ubuntu:20.04

RUN apt-get update && \
    apt-get install -y nginx && \
    apt-get clean
```

> Note: Use the backslash `\` with the `RUN` instruction to define line continuation. This divides a long command into multiple lines and improves readability.

Here is the basic syntax:

```dockerfile
RUN <command>
```

- `<command>`: This is used to specify the command you want to execute inside the container. Use the `RUN` instruction to execute a typical shell command or a script.

#### EXPOSE

Use the `EXPOSE` instruction to tell Docker which port the container will listen on at runtime. The instruction is mainly used for documentation purposes. 

For example, you can use the `EXPOSE` instruction to expose the application over port `80` inside the container:

```dockerfile
FROM ubuntu:20.04

# some other instructions

EXPOSE 80
```

> Note: Since you did not specify a protocol, the port declaration is treated as TCP i.e. `80/tcp`.

Here is the basic syntax:

```Dockerfile
EXPOSE <port> [<port>/<protocol>]
```

- `<port>`: This is used to specify the port number that the container will listen on.
- `<protocol>`: This is an optional parameter to specify the protocol for communication (e.g., TCP or UDP). The default protocol used is TCP.

As a further step when running the container, use the `--port host_port:container:port` or `-p host_port:container:port` flag to map the container port to a corresponding host port of choice.

#### CMD

Use `CMD` instruction like the `ENTRYPOINT` instruction to specify the default command to execute when a container runs. The difference is that if you use multiple `CMD` instructions, only the last one will get executed. The specified command can be overwritten by providing another command at runtime.

For example, you can use the `CMD` instruction to start the Nginx container in the foreground:

```dockerfile
FROM ubuntu:20.04

# some other instructions

CMD ["nginx", "-g", "daemon off;"]
```

Here is the basic syntax:

```Dockerfile
CMD ["command", "parameter1", "parameter2", ...]
```

```Dockerfile
CMD command param1 param2
```

- `command`: This is used to specify the command to execute.
- `parameter1 parameter2 ...`: This is used to specify the arguments or parameters of the command you want to execute.

#### ENTRYPOINT

Use the `ENTRYPOINT` instruction in place of the `CMD` instruction to specify the command that will be executed when a container is started. Unlike `CMD`, the specified command cannot be overwritten by providing another command at runtime. 

For example, you can use the `ENTRYPOINT` instruction to echo the word "Hello" when the container runs:

```dockerfile
FROM ubuntu:20.04

ENTRYPOINT ["echo", "Hello,"]
```

> Note: The `ENTRYPOINT ["echo", "Hello,"]` instruction is similar to running the `echo Hello,` command.

Here is the basic syntax:

```Dockerfile
ENTRYPOINT ["command", "param1", "param2", ...]
```


```Dockerfile
ENTRYPOINT command param1 param2 ...
```

- `command`: This is used to specify the command to execute.
- `parameter1 parameter2 ...`: This is used to specify the arguments or parameters to the command you want to execute.

You can provide an additional argument to the `ENTRYPOINT` instruction at runtime. 

For example, you can pass the extra parameter `Class` which will in turn give us the output `"Hello, Class"`:

```bash
docker run ubuntu:20.04 Class
```

### Building an image locally

Now that you have a clearer picture of what Docker images are and what Dockerfile files are made up of, you can build your first custom image.

Building a Docker image involves two major steps:

1. Defining a Dockerfile that executes specified instructions to create your new image. 

2. Using the `docker build` command to build an image from your Dockerfile.

Here is the syntax of the `docker build` command:

```bash
docker build -t image_name:tag .
```

- `-t`: This is used to specify a name/tag for the new image.
- `image_name:tag:` This is the name and tag for the image.
- `.`: This is the build context, where the Dockerfile and other necessary files are located. It could be the current directory `.` or any specified path e.g. `/path/to/directory`.

> Note: In the case where the Dockerfile is located in a different directory to the application code, you can also specify a different path for your Dockerfile by using the `-f` flag.

#### Exercise: Define steps to build an application

Suppose you have your application code ready and you want to turn that into a Docker image, you will need to follow some steps. The steps will usually include the following:

1. Identifying the base image.
2. Defining the steps required to build a sample application from the source code.
3. Identifying the application dependencies, if any.
4. Identifying the environment settings or custom configurations for the application.
5. Translating the defined steps into a Dockerfile, using appropriate Dockerfile instructions for each step.
6. Building an image using the `docker build` command.

##### Exercise 1: Building a Simple Java Application

https://github.com/devopshobbies/docker-templates?tab=readme-ov-file

Take things a step further by building a sample Java application `learning_docker.java` that contains the following code.

```java
import java.util.Scanner;

public class LearningDocker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Please enter your name:");
        String name = scanner.nextLine();

        System.out.println("Hello, " + name + "! Do you agree that Docker is important for efficient software delivery? (yes/no)");
        String response = scanner.nextLine();

        if (response.equalsIgnoreCase("yes")) {
            System.out.println("Great! Docker is a platform that allows you to automate the deployment, scaling, and management of applications using containerization. You will do more interesting things with it.");
        } else if (response.equalsIgnoreCase("no")) {
            System.out.println("That's okay, " + name + ". Docker is almost becoming the industry standard for packaging applications. It's a powerful tool that can make managing and deploying applications much easier!");
        } else {
            System.out.println("I didn't understand your response. Please answer with 'yes' or 'no'.");
        }

        scanner.close();
    }
}
```

> Note: This application does not listen on any port.

Follow these steps to achieve the desired image for the sample Java application:

1. Define the base image to use:

Select the `openjdk:11` image as a base image for the application. (Use the `FROM` instruction to achieve this).

2. Define the steps required to build the sample application from the source code:

Build the application using these steps:

- Define the working directory for the application. (Use the `WORKDIR` instruction to achieve this).
- Copy the application code `learning_docker.java` to the container. (Use the `COPY` instruction to achieve this).
- Compile the Java source code using the `javac` command. (Use the `RUN` instruction to achieve this).
- Package the compiled Java classes into a JAR file using the `java` command. (Use the `CMD` instruction to achieve this).
- Expose the port where the application will listen on, if applicable. (Use the `EXPOSE` instruction to achieve this).

3. Identify dependencies, if any:

There are no dependencies since it is a simple application.

4. Identify the environment settings or custom configurations for the application, if any.

There are no environment settings since it is a simple application.

5. Translate the defined steps into a Dockerfile, using appropriate Dockerfile instructions for each step:

Write the Dockerfile to include the base image and then the listed steps necessary to build the application:

```Dockerfile
# Use an image with JDK pre-installed
FROM openjdk:11

# Set the working directory
WORKDIR /app

# Copy the Java source code into the container
ADD . /app

# Compile the Java source code
RUN javac LearningDocker.java

# Define the command to run the Java application
CMD ["java", "LearningDocker"]
```

6. Build an image using the `docker build` command.

Build the image as follows:

```bash
docker build -t java_sample .
```

Run `docker images` command to confirm that the `java_sample` image is now available.

```
docker run -it java_sample
```

Enter your name at the prompt and enjoy the corresponding message depending on if you choose yes or no.

##### Exercise 2: Building a Simple Node.js Application

Let us assume that you have a second application written in NodeJS `sample.js` with the following code:

```js
const express = require('express');
const Parser = require('rss-parser');
const parser = new Parser();

const TED_TALKS_RSS_FEED = 'https://feeds.feedburner.com/TEDTalks_video';

const app = express();
const port = 3000;

app.get('/', async (req, res) => {
  const feed = await parser.parseURL(TED_TALKS_RSS_FEED);
  let talks = feed.items.map(item => ({
    title: item.title,
    link: item.link,
    snippet: item.contentSnippet
  }));
  res.json(talks);
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

> Note: This application listens on port `3000` and it also bundles with the following package.json:

```json
{
    "name": "ted-talks-feed",
    "version": "1.0.0",
    "description": "A simple application that serializes the recent TED Talks.",
    "main": "sample.js",
    "scripts": {
      "start": "node sample.js"
    },
    "dependencies": {
      "express": "^4.17.1",
      "rss-parser": "^3.10.0"
    }
  }
```

Follow these steps to achieve the desired image for the sample NodeJS application:

1. Define the base image to use:

Select the `node:14` image as a base image for the application. (Use the `FROM` instruction to achieve this).

2. Define the steps required to build the sample application from the source code:

Build the application using these steps:

- Define the working directory for the application. (Use the `WORKDIR` instruction to achieve this).
- Copy the `package.json` file to the container. (Use the `COPY` instruction to achieve this).
- Run the `npm install` command to install the dependencies in the `package.json` file. (Use the `RUN` instruction to achieve this).
- Copy every other application code from the local machine to the container. (Use the `COPY` instruction to achieve this).
- Expose the port where the application will listen, if applicable. (Use the `EXPOSE` instruction to achieve this).
- Start the application by providing the relevant command to start a NodeJS application. (Use the `CMD` instruction to achieve this).

3. Identify dependencies, if any:

There are no dependencies since it is a simple application.

4. Identify the environment settings or custom configurations for the application, if any.

There are no environment settings since it is a simple application.

5. Translate the defined steps into a Dockerfile, using appropriate Dockerfile instructions for each step:

Write the Dockerfile to include the base image and then the listed steps necessary to build the application:

```Dockerfile
# Use Node:14 as the base image
FROM node:14

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json into the container at /app
COPY package*.json ./

# Install the application dependencies
RUN npm install

# Copy the rest of the application's source code into the container at /app
COPY . .

# Make port 3000 available to the outside world
EXPOSE 3000

# Define the command to run the application
CMD [ "npm", "start" ]
```

6. Build an image using the `docker build` command.

Build the image as follows:

```bash
docker build -t node_sample .
```

Run `docker images` command to confirm that the `node_sample` image is now available.


Here is a sample output:

```
node_sample   latest    e8728b1238cd   About a minute ago   858MB
```

## Pushing images to an image registry

You can build your images and then push them to Docker Hub for later use. To do this, use a combination of the `docker build` and `docker push` commands.

Push a copy of the sample NodeJS application to Docker Hub using the `docker build` and `docker push` command:

```bash
docker build -t username/node_sample:latest .
docker push username/node_sample:latest
```

> Note: First authenticate to Docker Hub by using the `docker login` command. Pull the image using a combination of image tag and DockerHub username e.g `myusername/node_sample:latest`.

Here's the basic syntax:

```bash
docker build -t username/image_name:tag .
docker push username/image_name:tag
```

## Analyzing an image

You can analyze a Docker image using the `docker image history` and `docker image inspect` commands. These commands help us to gain insights into how an image is constructed, its layers, and other metadata.

## Using the `docker image history` command:

Use the `docker image history` command to show an image's history, including the commands executed in each layer during the build process. 

For example, you can display the history of the sample NodeJS image, showing each command executed during its build process:

```bash
docker image history node_sample
```

Here is the basic syntax:

```bash
docker image history <image_name>
```

### Using the `docker image inspect` command:

Use the `docker image inspect` command to provide detailed information about an image, including its metadata, configuration, and layers. 

For example, you can display a detailed information about the sample NodeJS image, including its metadata and configuration: 

```bash
docker image inspect node_sample
```

The information is grouped into the following sections:

- Id: The unique identifier for the image.

- RepoTags: The tags associated with the image. In this case, it's tagged as `node_sample:latest`.

- Parent: The parent image of the image.

- Comment: Some information about the build process.

- Created: The timestamp indicates when the image was created.

- ContainerConfig: The configuration details for the container, including environment variables, command to run, working directory, and labels.

- Architecture, Variant, OS: The architecture, variant, and operating system of the image.

- Size: The size of the image in bytes.

- GraphDriver: The information about the graph driver used for managing image layers.

- RootFS: The details about the root filesystem of the image, including the layers.

- Metadata: Some additional metadata, such as the timestamp for the last tag time.

Here is the basic syntax:

```bash
docker image inspect <image_name>
```

## Removing images
When you no longer need an image, you can save system resources by removing such an image. The `docker image rm` command comes handy to achieve this. You can also use the `docker image prune` command to remove all images that are not associated with any running container.

The `docker image prune` command has the `-f` or `--force` flag that is used to skip the confirmation prompt and automatically remove all unused images:

```bash
docker image prune -f
```

To remove all images, including the ones that are currently used by containers, use the `-a` flag with the `docker image prune` command as follows:

```bash
docker image prune -a
```

> Note: We will explore how to use the `docker commit` and `docker diff` commands to make further changes to our containers in the next chapter.

# Best practices when working with images

Imagine that your team was tasked with containerize all existing application so as to drive more efficiency in software delivery. 

You have written Dockerfiles and used base images according to your requirements but later figured that there are been a couple of resource and security constraint since your implementation. Tracking things that you realized that you realized that although you have a working implementation, your choice of base image and other concerns have resulted in the current issue you are now facing.

Containerization provides a lot of advantages but you also need to be security-conscious and efficiency-minded when working with images. Here are some key points to keep in mind:

## Do not run commands as the root user

It's generally recommended to avoid running commands as the root user inside containers for security reasons. Instead, create a less privileged user within the Dockerfile and switch to that user using the `USER` instruction.

Here is an example that shows a setup of the `pgbouncer` service:

```Dockerfile
FROM public.ecr.aws/amazonlinux/amazonlinux:2023

#...

# Clone pgbouncer repository and install pgbouncer
RUN git clone https://github.com/pgbouncer/pgbouncer.git --branch "stable-1.19" && \
    git clone https://github.com/awslabs/pgbouncer-rr-patch.git && \
    cd pgbouncer-rr-patch && \
    ./install-pgbouncer-rr-patch.sh ../pgbouncer && \
    cd ../pgbouncer && \
    git submodule init && \
    git submodule update && \
    ./autogen.sh && \
    ./configure --prefix=/usr/local --exec-prefix=/usr/bin --bindir=/usr/bin && \
    make && \
    make install

# Install the pgbouncer service using the pgbouncer user instead of root
RUN useradd -ms /bin/bash pgbouncer && \
    chown pgbouncer /home/pgbouncer && \
    chown pgbouncer /

USER pgbouncer
WORKDIR /home/pgbouncer
```

## Tag images appropriately

Tagging is very crucial and it helps indicate the different versions of an application. It is important for us to avoid the use of generic tags like `latest`. Use specific version numbers or environment instead e.g `1.0.0` and `dev`.

```bash
docker build -t image:1.0 .
```

## Use a `.dockerignore` file (if needed)

Use Docker ignores files to specify files to exclude in the image. An example is when you are building a NodeJS application, exclude the `node_modules` from being pushed into source control. Other files can be excluded include the Git configuration file `.git` and the environment settings `.env`. 

For example, you can create a `dockerignore` file that exludes the files/folders `.git`, `node_modules` and `.env` from getting pushed to a remote repository:

```bash
.git
node_modules
.env
```

## Use light base images as much as possible

The more the size of the base image, the more the overall size of the final image. Consider using lightweight base images like Alpine Linux or distroless images as much as possible.

For example, you can use the `alpine:3.14` image which is a lightweight Linux image to install and start `mysql` database:

```dockerfile
FROM alpine:3.14
RUN apk add --no-cache mysql-client
ENTRYPOINT ["mysql"]
```

## Format multiline commands properly

When you are required to have multiple commands chained together, ensure proper formatting to improve readability and maintainability. Use `&&` to join commands together and also use `\` to indicate a line end. This makes the Dockerfile more readable. 

For example, you can use the `\` to make the necessary commands for installing Nginx in the container more readable:

```Dockerfile
FROM ubuntu:16.04

LABEL MAINTAINER name@developer.pragmaticprogrammers.com

RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf

ADD default /etc/nginx/sites-available/default

EXPOSE 80
CMD ["nginx"]
```

## Separate concerns and use comments in Dockerfile

It is a very good practice to use comments in Dockerfiles. Comments are preceeded by `#` and helps to improve readability. Also, related instructions should be grouped together and actions should be arranged sequentially. 

For example, you can include necessary comments for each group of instructions in the Dockerfile:


```Dockerfile
# Define base image
FROM node:14 AS builder

# Install dependencies
WORKDIR /app
COPY package*.json ./
RUN npm install

# Copy source code and build app
COPY . .

# Expose application on the right port
EXPOSE 3000

# Run application
CMD ["npm", "start"]
```

## Do not install unnecessary packages

To keep the size of an image as light as possible, avoid the installation of unwanted packages. You can achieve this using the `--no-install-recommends` flag with the `apt-get install` command. 


For example, you can use the `-y --no-install-recommends` flag to only install the necessary packages and dependencies for a `Go` application:

```Dockerfile
FROM gcr.io/gcp-runtimes/ubuntu_20_0_4

RUN apt-get update && apt-get install -y --no-install-recommends \
		gcc \
		libc6-dev \
		make \
		pkg-config \
		curl \
		libvirt-dev \
		git \
	&& rm -rf /var/lib/apt/lists/*

ARG GO_VERSION

RUN curl -sSL https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz | tar -C /usr/local -xzf -

ENV GOPATH /go
ENV PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/go/bin:/go/bin
```

> Note: Use `&& rm -rf /var/lib/apt/lists/*` to clear out the package list files and reduce the size of your image.

## Use ADD and COPY command appropriately

Use the `COPY` instruction for copying local files and directories and use ADD instruction only when you need to copy remote files or automatically extract compressed files.

## Expose the right port

Expose the correct port on which an application is listening. Not exposing the right port can cause the application to be unreachable.

```Dockerfile
FROM nginx:alpine
LABEL maintainer="Me"

EXPOSE 80/tcp
EXPOSE 80/udp

CMD [ "nginx","-g","daemon off;" ]
```

## Using multistage builds (if required)

Utilize multistage builds to create a lighter and optimized image and also separate concerns in the build process. 

You can write a updated Dockerfile with multistage build for the NodeJS application:

```Dockerfile
# Stage 1: Build the application
FROM node:14 AS build

WORKDIR /app

# Copy package.json over to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Stage 2: Create a lightweight image
FROM node:14-alpine

WORKDIR /app

# Copy only the built artifacts from the first stage
COPY --from=build /app/build ./build
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app/package.json ./

# Expose necessary port
EXPOSE 3000

# Start application
CMD ["npm", "start"]
```

In this example, you create two stages as follows:
1. Stage 1: 

Use the node:14 image as the base and set the working directory. Then copy the ``package.json` and `package-lock.json` files and then run `npm install`. Conclude the stage by copying the application folder `/app` into the container and then running a build using `npm run build`.

2. Stage 2:

Use the `node:14-alpine` (a lightweight image) and set the working directory as necessary. Then copy the build artifacts (`/app/build`, `/app/node_modules` and `/app/package.json`) from the previous stage `build`. Conclude the stage by exposing the exposes the necessary port and specify the command to run the application.

# Chapter Summary

You explored how paramount dockerization is and how Docker images help to drive efficiency in software development. You learnt to write docker images and run them; following standard practice to enhance the overall image build process and time.

You learnt how to pull images, create different image versions using tags, push images to a remote repository, list images, run images and remove unused images.

In the next chapter, you will learn more about running images as containers, making changes to a running container, configuring networking and data persistence amongst other things.
