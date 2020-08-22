In this step, we shall describe the `resource_template` file. This describes all the resources needed by the modules in the pipeline.

Broadly speaking, there are two types of resources: docker images and other files need by the modules. The docker images need to be available in an online docker repository and the other files need to be accessible from Google (GCP) cloud storage.

<pre class="file" data-filename="EXAMPLE_resource_template.config" data-target="replace">
[Docker]
    [[example]]
        image = davelabhub/example_docker:1.0

[Path]
    [[example_resource]]
        resource_type   = example_resource
        path            = gs://davelab_data/ref/example.bed
</pre>

The docker image mentioned here is the one that we created in the first tutorial. The example_resource is shown to illustrate the manner in which we can access resources from cloud storage.

Next, we shall see how we inform the module that it can access this docker image that we have created.