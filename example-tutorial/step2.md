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

Next, we fill in the metadata information:
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
    git
    python3-pip \
    gawk \
    bedtools
</pre>

You can use the `RUN` prefix to install any other dependencies that your code might have. For example,
<pre class="file" data-filename="Dockerfile" data-target="append">RUN pip3 install argparse
</pre>