Docker can build images automatically by reading the instructions from a Dockerfile, a text file containing all the commands, in order, needed to build a given image. Dockerfiles adhere to a specific format and use a specific set of instructions. You can find the Dockerfile reference [here](https://docs.docker.com/engine/reference/builder/).

In this step, we shall create a Dockerfile. The first step is to choose a base layer - for most cases, a base Linux image should work. 

<pre class="file" data-filename="Dockerfile" data-target="replace"># work from the latest LTS ubuntu release
FROM ubuntu:18.04
</pre>

You may need to use a different base image depending on your requirements. Suppose you need to have R installed for your scripts to run, instead of installing R manually, you can choose to start from an image which has R installed.

<pre class="file" data-filename="Dockerfile" data-target="replace"># work from R version 3.6
FROM r-base:3.6.0
</pre>

Next, we fill in the metadata information:
<pre class="file" data-filename="Dockerfile" data-target="append"># Metadata
LABEL software="example"
LABEL software.version="1.0.0"
LABEL description="An example Dockerfile"
LABEL maintainer="lab.dave@gmail.com"
</pre>

The default base image you start from is usually rather bare-bones, so the next step is to install some basic required packages. You may need to install more packages based on the requirements of your scripts.
<pre class="file" data-filename="Dockerfile" data-target="append"># update the OS related packages
RUN apt-get update -y && apt-get install -y \
    build-essential \
    curl \
    vim \
    less \
    wget \
    unzip \
    cmake \
    gcc-8-base \
    git \
    python3-pip \
    gawk \
    bedtools
</pre>

You can use the `RUN` prefix to install any other dependencies that your code might have. For example,
<pre class="file" data-filename="Dockerfile" data-target="append"># install any other dependencies needed
RUN pip3 install argparse
</pre>

In the Step 1, we had ensured that our scripts were available online in a git repo. Having set up our environment, we now import our scripts from the git repo using `git clone`.

`git clone https://github.com/<USER>/<REPO>.git`{{copy}}

It is crucial to be noted that while updating an image, Docker only executes commands where the command or the output of the command has changed. Since changes to the git repo are not reflected in the result of a successful clone response status, Docker has no way of knowing if the git repo has changed. An easy way out is to query the last commit made to the repo and store it. This way, Docker will clone the directory if it has had any commits since the previous build.

<pre class="file" data-filename="Dockerfile" data-target="append"># clone git repo
ADD https://api.github.com/repos/DevangThakkar/dockerized_scripts/git/refs/heads/ version.json
RUN git clone https://github.com/devangthakkar/dockerized_scripts.git /repo
RUN cp /repo/example_scripts/* /
</pre>

Your Dockerfile is now ready! Ensure that the file has no extensions, i.e. the file is named simply `Dockerfile`.