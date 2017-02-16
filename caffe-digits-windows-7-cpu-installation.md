Installing [Caffe](http://caffe.berkeleyvision.org/) + [DIGITS](https://developer.nvidia.com/digits) for CPU in Windows 7/8/10
==============================================

Instructions to install DIGITS to follow [@humphd's "Have Fun with Machine Learning: A Guide for Beginners"](https://github.com/humphd/have-fun-with-machine-learning/blob/master/README.md).

This instructions also apply for Windows 8 and 10, Home edition.

[Docker for Windows](https://www.docker.com/products/docker#/windows) requires Microsoft Windows 10 Professional or Enterprise 64-bit.

For previous versions, we need to install [Docker Toolbox](https://www.docker.com/products/docker-toolbox).

Docker Toolbox is easy to install (small guide [here](http://www.htpcbeginner.com/install-docker-on-windows-7-8-10/)).

Pay special attention to the step where you need to [Enable hardware virtualization VT-x/AMD-V in BIOS or UEFI](http://www.htpcbeginner.com/enable-hardware-virtualization-vt-x-amd-v/).

After Docker Toolbox is installed, launch Kinematic and install the kaixhin/digits image.

Then launch Docker Quickstart Terminal, and run 

    docker run -d -v <repo path>/data:/tmp/images -p 34448:5000 --name linked-digits kaixhin/digits

This will start our Digits image with a link to the repo so we can use the images in it to train our model.

It's important to notice that the path must be formatted like this:

If I cloned the repo at

    C:\Users\Alejandro\have-fun-with-machine-learning\

The command will look like this:

    docker run -d -v //c/Users/Alejandro/have-fun-with-machine-learning/data:/tmp/images -p 34448:5000 --name linked-digits kaixhin/digits

After that command is executed, the instance will appear in Kinematic with the name 'linked-digits'

In the Volumes tab in the right, you should see the linked folder.

Do not worry if you see this message in the console output, it's just a warning as far as I know:

    libdc1394 error: Failed to initialize libdc1394

To browse to the Digits instance running in your browser, click the Web Preview button in Kinematic.

In my case the address was http://192.168.99.100:34448/
