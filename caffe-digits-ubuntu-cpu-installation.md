Installing [Caffe](http://caffe.berkeleyvision.org/) + [DIGITS](https://developer.nvidia.com/digits) for CPU in Ubuntu 16.04
==============================================

Instructions to install DIGITS to follow [@humphd's "Have Fun with Machine Learning: A Guide for Beginners"](https://github.com/humphd/have-fun-with-machine-learning/blob/master/README.md).

[Install Docker for Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)

[nvidia/digits](nvidia/digits) is the docker image for GPU (CUDA) enabled Caffe, for CPU, use [kaixhin/digits](https://hub.docker.com/r/kaixhin/digits/) instead

In your console:

    docker pull kaixhin/digits

    docker run -d -p 34448:5000 kaixhin/digits

(wait a few seconds for the server to get up)

browse [http://localhost:34448](http://localhost:34448)

DIGITS should load

clone repo

    cd <repo path>

    git clone git@github.com:humphd/have-fun-with-machine-learning.git

List the dockers running:

    docker ps

Look up the nvidia/digits CONTAINER ID and stop it:

    docker stop <container id>

Connect the images folder to the docker instance:

    docker run -d -v <repo path>/have-fun-with-machine-learning/data:/tmp/images -p 34448:5000 kaixhin/digits

Now DIGITS has access to /tmp/images with all the images in the repo.

Follow the @humphd's guide to create dataset and model.

When training the model using CPU, some computers might hang completely, consuming 100% CPU and memory, just wait for it.
