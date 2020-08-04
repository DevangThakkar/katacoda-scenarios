In this step, we shall describe the define\_input() function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_input(self):
		self.add_argument("bam",				is_required=True)
		self.add_argument("nr_cpus",			default_value=1)
		self.add_argument("mem",				default_value=5)

</pre>

There are a few talking points in this snippet. In the `add_argument()` call, there are certain parameters that need to be discussed.

* `is_required=False`: This parameter is set to True if the module explicitly requires this input
* `default_value=None`: This parameter describes the default value of the input
* `is_resource=False`: This parameter describes if the input is specified in the resource kit - we shall describe what a resource kit is in the next tutorial.

The `nr_cpus` and `mem` arguments are expected to be set by CloudConductor, therefore it is standard practice to set a default value in the module.