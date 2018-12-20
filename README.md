# Collective Knowledge Workflows for Movidius Neural Compute Stick

[![compatibility](https://github.com/ctuning/ck-guide-images/blob/master/ck-compatible.svg)](https://github.com/ctuning/ck)
[![automation](https://github.com/ctuning/ck-guide-images/blob/master/ck-artifact-automated-and-reusable.svg)](http://cTuning.org/ae)
[![workflow](https://github.com/ctuning/ck-guide-images/blob/master/ck-workflow.svg)](http://cKnowledge.org)

[![DOI](https://zenodo.org/badge/110333824.svg)](https://zenodo.org/badge/latestdoi/110333824)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

# Introduction
This repository contains [Collective Knowledge workflows](http://cKnowledge.org/ai) 
to automate installation and execution of AI applications 
for [Movidius Neural Compute Stick](https://developer.movidius.com/start).

It also contains wrappers for YOLO object detection example 
from [this GitHub repository](https://github.com/gudovskiy/yoloNCS).

# Installing CK

The minimal installation requires:

* Python 2.7 or 3.3+ (limitation is mainly due to unitests)
* Git command line client.

You can install CK in your local user space as follows:

```
$ git clone http://github.com/ctuning/ck
$ export PATH=$PWD/ck/bin:$PATH
$ export PYTHONPATH=$PWD/ck:$PYTHONPATH
```

You can also install CK via PIP with sudo to avoid setting up environment variables yourself:

```
$ sudo pip install ck
```

# Installing MVNC CK workflow on Linux

```
$ ck pull repo:ck-mvnc

$ ck install package --tags=lib,mvnc
$ ck install package --tags=caffemodel,yolo,tiny
$ ck install package --tags=demo,mvnc,yolo
```

# Detecting device via CK

```
$ ck detect platform.npu
```

Sharing info with the community:
```
$ ck detect platform.npu --share
```

##  Raspberry Pi notes

Note that Movidius Neural Compute Stick can run only on Raspbian Stretch or above. 
You can download this image for your RPi [here](https://www.raspberrypi.org/downloads/raspbian).

Since this OS version doesn't have integrated OpenCV support in Python 3, you will need
to answer "yes" to build OpenCV when installing MVNC package. It will take a very long
time (sometimes more than an hour) but it may be worth it.

# Running example with YOLO image classification
```
$ ck compile program:demo-mvnc-yolo
$ ck run program:demo-mvnc-yolo --cmd_key=classify-objects-in-images
```

# Running example with YOLO object detection from a webcam
```
$ ck compile program:demo-mvnc-yolo
$ ck run program:demo-mvnc-yolo --cmd_key=classify-objects-in-webcam
```

You can change webcam ID with width and height as follows:
```
$ ck run program:demo-mvnc-yolo --cmd_key=classify-objects-in-webcam --env.SRC=1 --env.WD=800 --env.HT=600
```

# Running internal Movidius examples
```
$ ck run program:demo-mvnc-yolo --cmd_key=run-internal-movidius-examples
```

# Further reading about unified AI project

http://cKnowledge.org/ai
