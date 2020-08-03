Docker can build images automatically by reading the instructions from a Dockerfile, a text file containing all the commands, in order, needed to build a given image. Dockerfiles adhere to a specific format and use a specific set of instructions.

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
MAINTAINER DaveLab <lab.dave@gmail.com>
</pre>