In this step, we shall describe the `graph_template` file. We had linked to [this graph](https://github.com/DevangThakkar/dockerized_scripts/blob/master/example_scripts/CNV_Pipeline.svg) back in Step 1 to explain what a pipeline looks like - this file defines that graph. Since our example pipeline is going to consist only of one module, the pipeline graph will look rather simple.

<pre class="file" data-filename="EXAMPLE_graph_template.config" data-target="replace">
[example]
    module                      = Example
    submodule                   = Example
    docker_image                = example_docker
    final_output                = header_lines, header_chars
</pre>

Line 1 (`[example]`) defines the name of the module in the pipeline - it is standard practive to have it be the same as the module name.

Line 2 (`Example`) lists the module name - this is the name of the Module file (minus the `.py`) that we created in our previous tutorial

Line 3 (`Example`) lists the submodule name which for common use cases is the same as Line 2. To be precise, this is the name of the class in the Module file. This functionality is provided to group together several related submodules as different classes in the same Module file, however, you should usually be good with the `submodule` being the same as the `module`.

Line 4 (`example_docker`) lists the docker image that we have created. The value here links to the resource that was defined in the previous step.

Line 5 (`header_lines, header_chars`) lists the final outputs from the module. This is the same as the output keys defined in Step 2 of the previous tutorial.

Another important feature of the graph is the linkage between modules. We can add edges between modules by specifying the `input_from` argument. We can also make input arguments take values besides their default values specified in the module. For example, if we need more memory than the default value specified in the module, we can set it here.

A mock graph config file with two modules is shown below for better understanding. Note the usage of `input_from` and `[[args]]`. 

`
[example]
    module                      = Example
    submodule                   = Example
    docker_image                = example_docker
    final_output                = header_lines, header_chars
    [[args]]
        mem						= 10
[second_example]
    module                      = Example2
    submodule                   = Example2
    docker_image                = example2_docker
    final_output                = header_lines, header_chars
    input_from					= example
`

Next, we shall learn how the pipeline accesses sample-specific files in the sample sheet.