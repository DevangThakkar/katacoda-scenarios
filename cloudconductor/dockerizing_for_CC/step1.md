The first step towards making your pipeline/module is having the code dockerized. Dockerizing your code allows you to

* create an API in order to interact with your code
* make changes to your code with minimal or no changes to your module
* implement version control

If you're following along on your own, make sure you have pushed the requisite files to a git repository before you proceed to the next step. The idea here is that the Docker container should be able to access the files from a remote location on the web - a git repository is the ideal solution for this.

If you're simply following along with this tutorial, you're all set. For this tutorial, we shall be using the script present [here](https://github.com/DevangThakkar/dockerized_scripts/blob/master/example_scripts/script.sh). This script counts the number of lines and characters in the header of BAM file provided to it.

