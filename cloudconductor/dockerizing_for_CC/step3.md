Having created a Docekrfile in Step 2, we shall now build a Docker image using this Dockerfile. I shall refrain from explaining the relation between a Dockerfile, a Docker image and a Docker container for the sake of brevity. You can check out other courses such as [this](https://katacoda.com/loodse/courses/docker) to learn more about how Docker works.

Check out the contents of the Dockerfile by running the following command:

`cat Dockerfile`{{execute}}

To ensure that Docker is running, we can use

`docker version`{{execute}}

If Docker is correctly installed, you will see output of the sort

`Client:
 Version:           19.03.6
 API version:       1.40
 ...`

We can build a Docker image from the Dockerfile using the shown command below. Building a Docker image for the first time takes a while but future re-builds are much faster due to caching of unchanged layers.

`docker build -t davelabhub/example_docker:1.0 .`{{execute}}

The `-t` flag takes in the image name which is of the form shown below; you will need to edit these variables for your use case.

`$CONTAINER_REGISTRY/$IMAGE:$TAG`{{copy}}

We shall talk more about the container registry in Step 5. 

To see confirm that our iamge was successfully built, we can look at the list of docker images on our system

`docker images`{{execute}}

You should be able to see the REPOSITORY `davelabhub/example_docker` with the TAG `1.0` at the top of the list.

Congratulations! You have now built your Docker image.