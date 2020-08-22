In this step, we shall describe the `sample_sheet` file. The sample sheet describes the input to the pipeline.

<pre class="file" data-filename="EXAMPLE_sample_sheet.json" data-target="replace">
{
    "samples": [
        {
            "paths": {
                "bam": {
                    "operation": "AND",
                    "values": ["filtersamreads", "nonspliced", "dna"]
                },
                "bam_idx":  {
                    "operation": "AND",
                    "values": ["filtersamreads", "nonspliced", "dna"]
                }
            }
        }
    ]
}
</pre>

This sample sheet allows you to select the non-spliced DNA BAM file from an upstream analysis. For most analyses starting from an upstream analysis, this file would not need any modifications.

This marks the completion of the pipeline creation!

`mkdir cc-config-templates/EXAMPLE
cp EXAMPLE*.config cc-config-templates/EXAMPLE/
cp EXAMPLE*.json cc-config-templates/EXAMPLE/`{{execute}}

You can then commit the changes and push to the repo if you have pushing privileges!