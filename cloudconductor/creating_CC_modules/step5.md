In this step, we shall describe the `define_command()` function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_command(self):
		bam 					= self.get_argument("bam")
		out 					= self.get_output("header_count")

		cmd = "bash /script.sh -b {0} -o {1}".format(bam, out)

		# add logging
		cmd += "!LOG3!"

		return cmd

</pre>

When generating the command, you can use the following placeholders and CloudConductor will create a log file for you:

* `!LOG0!` - pipes the stdout and strerr to /dev/null
* `!LOG1!` - pipes only the stdout to a log file that will be available after the module finished running
* `!LOG2!` - pipes only the stderr to a log file that will be available after the module finished running
* `!LOG3!` - pipes both the stdout and the stderr to a log file that will be available after the module finished running

This marks the completion of the module creation!

An important point to be noted is that no module development should should occur directly on the `master` branch. We can checkout a branch by using the `git  checkout <branchname>`{{copy}} command.

The module, depending on whether it is a `Tool`, `Merger`, or `Splitter`, belongs in the respective folder in the CloudConductor repo. Since our tool is a simple Module/Tool, we can place it in the appropriate directory using the following command:

`cp Example.py CloudConductor/Modules/Tools/`{{execute}}

You can then commit the changes and push to the repo if you have pushing privileges!