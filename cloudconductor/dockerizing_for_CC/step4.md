Having built a Docker image in Step 3, we shall now proceed to test if our Docker runs as expected. Check if the docker image exists with the command `docker images`{{execute}}

You should be able to see the REPOSITORY `davelabhub/example_docker` with the TAG `1.0` at the top of the list.

In order to run our docker image, we can use multiple commands. One way is to use `docker run`

`docker run --rm --user root -v "${PWD}:/data" davelabhub/example_docker:1.0 /bin/bash -c "bash script.sh"`{{execute}}

Here, 

1. `docker run` runs the docker image as a container
2. `--rm` deletes the container after execution
3. `--user root` indicates the user profile in the container
4. `-v` mounts the current working directory into the container
5. `"${PWD}:/data"` mounts the current working directory into `/data`
6. Finally, the command is passed as an argument to the `/bin/bash` shell

This is the ideal way to confirm if the docker container runs as expected. However, sometimes, we may need to look inside the docker for debugging purposes. In order to do so, we can run the docker container in an interactive fashion.

`docker run -it davelabhub/example_docker:1.0`{{execute}}

We are now inside the docker container! There are other ways to access a docker container, but these two methods should be enough for scope of this course. 
