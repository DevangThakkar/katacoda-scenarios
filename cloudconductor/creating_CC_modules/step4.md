In this step, we shall describe the `define_output()` function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_output(self):
		header_count			= self.generate_unique_file_name("header_count.txt")
		self.add_output("header_count",	header_count)

</pre>

By this point, you should be able to figure out what this snippet is trying to do. We create a file with a unique name containing the term `header_count.txt` and link the file to the output key `header_count`.