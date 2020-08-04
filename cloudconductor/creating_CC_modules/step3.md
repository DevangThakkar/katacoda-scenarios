In this step, we shall describe the define\_input() function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_input(self):
		# Module creator needs to define which arguments have is_resource=True
		# Module creator needs to rename arguments as required by CC
		self.add_argument("vcf_gz",				is_required=True)
		self.add_argument("nr_cpus",			default_value=1)
		self.add_argument("mem",				default_value=5)
		self.add_argument("whitelist",			is_required=True, is_resource=True)
		self.add_argument("e",					default_value=False)
</pre>