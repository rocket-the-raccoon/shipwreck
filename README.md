## ShipWreck

### Procedure to get ROS Kinetic Docker

- ```docker pull osrf/ros:kinetic-desktop-full``` To download a new docker **image**.
- ```docker run osrf/ros:kinetic-desktop-full``` To create a **container** out of an image.
- ```docker run -it osrf/ros:kinetic-desktop-full``` To create a container and enter it.
- ```docker run -it osrf/ros:kinetic-desktop-full roscore``` To create a container and start the **rosmaster**.

#### Publishing Messages
Open three terminals and type the following:\
**Terminal 1**
```
docker run -it --net=host osrf/ros:kinetic-desktop-full roscore
```
**Terminal 2**
```
docker run -it --net=host osrf/ros:kinetic-desktop-full bash
# Enter the bash
rostopic pub -r 1 /my_topic std_msgs/String '{data: "hello"}'
```
**Terminal 3**
```
docker run -it --net=host osrf/ros:kinetic-desktop-full bash
rostopic echo /my_topic
```
This should publish the messages
```
data: "hello"
---
data: "hello"
```

#### Definitions/Notes
**Dockerfile** : A dockerfile is a configuration file for a docker container which helps install all the necessary prereqs and set up the workspace.\
A good example of a Dockerfile is:
```
FROM ubuntu:latest
MAINTAINER pruthvi

RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get install -y build-essential
RUN apt-get -y install git
RUN git clone https://github.com/rocket-the-raccoon/shipwreck.git
```
In a terminal running the follwing command helps build the container
```
 docker build -t "test:Dockerfile" .
```
To run the container
```
docker run -it test:Dockerfile bash
```
