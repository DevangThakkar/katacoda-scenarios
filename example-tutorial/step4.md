Having built a Docker image in Step 3, we shall now proceed to test if our Docker runs as expected. Check if the docker image exists with the command `docker images`{{execute}}

You should be able to see the REPOSITORY example_docker with the TAG 1.0 at the top of the list.

In order to run our docker image, we can use multiple commands. One way is to use `docker run`

`docker run --rm --user root -v "${PWD}:/data" example_docker:1.0 /bin/bash -c "python3 script.py"`{{execute}}

Here, 

1. `docker run` runs the docker image as a container
2. `--rm` deletes the container after execution
3. `--user root` indicates the user profile in the container
4. `-v` mounts the current working directory into the container
5. `"${PWD}:/data"` mounts the current working directory into `/data`
6. Finally, the command is passed as an argument to the `/bin/bash` shell