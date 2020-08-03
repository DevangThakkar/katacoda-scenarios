Docker can build images automatically by reading the instructions from a Dockerfile, a text file containing all the commands, in order, needed to build a given image. Dockerfiles adhere to a specific format and use a specific set of instructions.

In this step, we shall create a Dockerfile. The first step is to choose a base layer - for most cases, a base Linux image should work. 

<pre class="file" data-filename="Dockerfile" data-target="replace"># work from latest LTS ubuntu release<br>FROM ubuntu:18.04
</pre>

An example of when you would need to use a different 