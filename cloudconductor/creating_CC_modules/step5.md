In this step, we shall describe the `define_command()` function.

<pre class="file" data-filename="Example.py" data-target="append">

	def define_command(self):
		bam 					= self.get_argument("bam")
		lines 					= self.get_output("header_lines")
		chars 					= self.get_output("header_chars")

		cmd = "bash /script.sh -b {0} -l {1} -c {2}".format(bam, lines, chars)

		# add logging
		cmd += "!LOG3!"

		return cmd

</pre>

Having set the arguments and the outputs in the previous functions, we now need to get them in this function so that we can use them in our command. This encapsulation of arguments and outputs is a key component of CloudConductor.

When generating the command, you can use the following placeholders and CloudConductor will create a log file for you:

* `!LOG0!` - pipes the stdout and strerr to /dev/null
* `!LOG1!` - pipes only the stdout to a log file that will be available after the module finished running
* `!LOG2!` - pipes only the stderr to a log file that will be available after the module finished running
* `!LOG3!` - pipes both the stdout and the stderr to a log file that will be available after the module finished running

When in doubt, use `!LOG3!` to save both standard output and standard error.

This marks the completion of the module creation!

An important point to be noted is that no module development should occur directly on the `master` branch. We can checkout a branch by using the `git  checkout <branchname>`{{copy}} command.

The module, depending on whether it is a `Tool`, `Merger`, or `Splitter`, belongs in the respective folder in the [CloudConductor repo](https://github.com/labdave/CloudConductor/tree/master/Modules). Since our tool is a simple Module/Tool, you will have to place it in the appropriate directory using the following command:

`cp Example.py CloudConductor/Modules/Tools/`{{execute}}

You can then commit the changes and push to the repo if you have pushing privileges!