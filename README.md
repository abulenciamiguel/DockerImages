# How to create a docker image and push it to docker hub.

### Create a directory with a blank file named "Dockerfile". <br>
```
mkdir chopper

nano chopper/Dockerfile
```

> [!NOTE]
> You can choose any name for the directory. <br>
> You may choose another name for the docker file but the default name, i.e., "Dockerfile", as shown below is strongly suggested. <br>


Below shows five directories each containing a docker file to build the different images.
```
.
├── chopper
│   └── Dockerfile
├── kofamscan
│   └── Dockerfile
├── medaka
│   └── Dockerfile
├── minimap2
│   └── Dockerfile
└── minimap2-samtools
    └── Dockerfile
```

### The anatomy of the Dockerfile
<details>
  <summary>Click me</summary>

```
# This is an image containing the OS.
# You can select other images with different OS at https://hub.docker.com/
FROM ubuntu:20.04                                      

# Pretty straightforward
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"

# Set to disable dialog pop ups during apt-get install
ARG DEBIAN_FRONTEND noninteractive


# The work directory. You may choose other directory in the container
WORKDIR /tmp


### Install required packages
# To install the "unzip" and "wget" tools
# Cleaning of temporary files is done to reduce the size of the container

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        unzip \
        wget && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


### Installing chopper
# Metadata of the container
ENV VERSION 0.7.0
ENV NAME "chopper"

# This is similar to how you would install the tool in your local environment
# To reduce the size, install from the pre-built binaries instead of conda

RUN wget https://github.com/wdecoster/chopper/releases/download/v0.7.0/chopper-musl.zip && \
    unzip chopper-musl.zip && \
    chmod +x chopper && \
    cp chopper /bin/ && \
    rm chopper*
```
</details>

### Assuming you have created a `Dockerfile` inside the `chopper` directory, build the image

```
cd chopper

docker build -t ufuomababatunde/chopper:v0.7.0 .
```
More details can be found at https://docs.docker.com/reference/cli/docker/image/build/

### Check then push the image
```
docker images

docker image push ufuomababatunde/chopper:v0.7.0
```