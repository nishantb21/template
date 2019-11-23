# Docker

This is where the "production" part of this repo comes in. Often we need to deploy the training onto a common server which probably has GPUs. The base directory contains the Dockerfile for the base image on top of which the rest of the Dockerfiles are built(hence the name). Since this repo assumes that the user is using CUDA and `conda`, a custom image is required which is based on CUDA and adds the `conda` command. Furthermore, it needs to recreate the environment in the image which is done by copying the `environment.yml` file created by conda(when you export the environment) into the image and running a restore inside the build. The Dockerfile ensures that the code does not run as root but as a user with the same user ID and group ID as the host system. Doing this ensures that any files created during the training are available to the user.

First build the base image using
```
docker build --no-cache --build-arg usr="$(id -u -n)" --build-arg usrid="$(id -u)" --build-arg grp="$(id -g -n)" --build-arg grpid="$(id -g)" -f ./dockerfiles/base/Dockerfile -t base .
```

Then build the training image using
```
docker build -f ./dockerfiles/train/Dockerfile -t train .
```

Finally, run the trainer in a docker container using
```
docker run -d --gpus 1 --name trainer --mount type=bind,source=<path on host>,destination=/code/save --mount type=bind,source=<path on host>,destination=<path config expects> train
``` 

For different production configurations, create a separate `prod` branch.