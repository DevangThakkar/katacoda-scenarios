Modules are an integral part of the CloudConductor platform. Modules are the building blocks of pipelines in CloudConductor. There are three types of modules in CloudConductor:

* Tool/Module - represents a tool that can have one or multiple functions, represented as submodules

* Splitter - represents a tool that splits one input data entity into multiple chunks of data of the same type

* Merger - represents a tool that merges chunks of data of the same type, into one output data entity

First, we shall clone the CloudConductor git repo from Github using the following command

`git clone https://github.com/labdave/CloudConductor.git`{{execute}}

A module has four essential functions. We shall talk more about these functions in the next steps. 

* `__init__()`

* `define_input()`

* `define output()`

* `define_command()`



The aim of this tutorial is to create a CloudConductor Module for the script that we had dockerized in the previous tutorial. The script performs the simple task of counting the number lines in the header of a BAM file that is passed to it.