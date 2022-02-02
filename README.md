## shipwreck

### Command
```docker pull``` command to pull the docker image.
When an image is pulled, only one image is pulled at a time. Multiple containers can be spawned from a single image.
The command ```docker image rm <image_name>``` removes the image. The command ```docker rm <container_name>``` removes a container.

- The command ```docker run <image_name>``` creates a new container from an image, everytime you run it.
- The command ```docker exec -it <container_name> /bin/bash``` allows to enter the container.\
Question: Does it assume the same properties as it was spawned using the ```docker run``` command?

