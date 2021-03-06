In this step, we shall describe the `__init__()` function. `__init__` is a Python constructor that allows us to initialize the attributes of the class.

As described earlier, the example script we want to modularize counts the number of lines and the number of characters in the header of a BAM file that is passed to it. Let us assume that we need these counts in files called `header_lines.txt` and `header_chars.txt` respectively.

<pre class="file" data-filename="Example.py" data-target="replace">
# Author: Devang Thakkar
# Last Modified by: Devang Thakkar

class Example(Module):
    def __init__(self, module_id, is_docker=False):
        super(Example, self).__init__(module_id, is_docker)
        
        # Add output keys here if reuired
        self.output_keys        = ["header_lines", "header_chars"]

</pre>

This snippet presents quite a few concepts that need to be explained. Here, `Example` is the name of the Module, and hence the name of the Python class. The keyword `Module` in `class Example(Module)` represents the type of tool - it can take any of the values `Module`, `Merger`, `Splitter` based on the type of tool.

The other important part in this snippet is `output_keys`. This variable stores the outputs from the module - in our case, we expect to store the number of lines in the header of a BAM file. The link between the file and the keyword will be made in a later step.
