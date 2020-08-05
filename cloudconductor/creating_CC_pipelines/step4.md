In this step, we shall describe the `define_output()` function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_output(self):
		header_lines			= self.generate_unique_file_name("header_lines.txt")
		header_chars			= self.generate_unique_file_name("header_chars.txt")
		self.add_output("header_lines",	header_lines)
		self.add_output("header_chars",	header_chars)

</pre>

By this point, you should be able to figure out what this snippet is trying to do. We create files with unique names containing the term `header_lines.txt` and `header_chars.txt` and link the files to the output keys `header_lines` and `header_chars` respectively.