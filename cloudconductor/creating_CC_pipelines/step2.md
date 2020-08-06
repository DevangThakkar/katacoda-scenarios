In this step, we shall describe the `platform_template` file - which is undeniably the simplest of the four files.

<pre class="file" data-filename="EXAMPLE_platform_template.config" data-target="replace">
zone                        = us-east1-c
randomize_zone              = False
service_account_key_file    = var/keys_GAP_new.json
report_topic                = pipeline_reports

[task_processor]
disk_image      = davelab-image-docker
max_reset       = 3
is_preemptible  = True
cmd_retries     = 2
apt_packages    = pigz, bc
</pre>

In almost all cases, you will not need to edit this file. An exception is when your script requires Annovar - in that case, you'll have to replace the disk image `davelab-image-docker` by `davelab-image-annovar-docker-hg38-new`{{copy}}.