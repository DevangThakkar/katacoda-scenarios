In this step, we shall describe the `define_input()` function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_input(self):
		self.add_argument("bam",		is_required=True)
		self.add_argument("nr_cpus",	default_value=1)
		self.add_argument("mem",		default_value=5)

</pre>

There are a few talking points in this snippet. In the `add_argument()` call, there are certain parameters that need to be discussed.

* is_required - sets if the input_key is mandatory (False by default)
* default_value - a default value for the input_key, in case it never gets set (None by default)
* is_resource - sets if the input_key represents a resource to be searched in resource kit (False by default) - we shall describe what a resource kit is in the next tutorial.

The `nr_cpus` and `mem` arguments are expected to be set by CloudConductor, therefore it is standard practice to set a default value in the module.