---
layout: page
title: The Unix Shell
subtitle: Shell scripts and variables
minutes: 30
---

> ## Learning Objectives {.objectives}
>
> *   Learn what a script is
> *   Write simple shell scripts
> *   Understand and manipulate UNIX permissions
> *   What is a comment?
> *   Understand shell variables and how to use them
> *   What is $PATH?
> *   Write a simple for loop

We now know a whole bunch of UNIX commands. Wouldn't it be great if we could save certain commands so that we could run them later or not have to type them out again? As it turns out, this is extremely easy to do. Saving a list of commands to a file is called a "shell script". These shell scripts can be run whenever we want, and are a great way to automate our work.

So how do we write a shell script, exactly? It turns out we can do this with a simple text editor. Start editing a file called "demo.sh" (`nano demo.sh`). The ".sh" is simply the standard file extension for shell scripts that people use.

Our shell script will have two parts:  

+ On the very first line, add `#!/bin/bash`. The `#!` (pronounced "hash-bang") tells our computer what program to run our script with. In this case, we are telling it to run our script with our command-line shell (what we've been doing everything in so far). If we wanted our script to be run with something else, like Python, we could add `#!/usr/bin/python`

+ Now, anywhere below the first line, add `echo "Our script worked!"`. When our script runs, `echo` will happily print out `Our script worked!`.

Our file should now look like this:

```{.bash}
#!/bin/bash

echo "Our script worked!"
```

Ready to run our program? There's one last thing we need to do. Before a file can be run, it needs "permission" to run. Let's look at our file's permissions with `ls -l` (remember this from earlier?).

```{.bash}
ls -l
```
```{.output}
-rw-r--r--. 1 hpcxxxx hpcgyyyy        39 Jan 27 10:45 demo.sh
-rw-r-----. 1 hpcxxxx hpcgyyyy    721242 Jan 25 11:09 dmel_unique_protein_isoforms_fb_2016_01.tsv
-rw-r--r--. 1 hpcxxxx hpcgyyyy 159401627 Jan 20 14:32 Drosophila_melanogaster.BDGP5.77.gtf
drwxr-xr-x. 2 hpcxxxx hpcgyyyy        18 Jan 25 13:53 fastq
-rw-r-----. 1 hpcxxxx hpcgyyyy  56654230 Jan 25 11:09 fb_synonym_fb_2016_01.tsv
-rw-r-----. 1 hpcxxxx hpcgyyyy   1830516 Jan 25 11:09 gene_association.fb.gz
-rw-r--r--. 1 hpcxxxx hpcgyyyy        15 Jan 25 13:56 test.txt
-rw-r--r--. 1 hpcxxxx hpcgyyyy       270 Jan 25 14:40 word_counts.txt
```

So what is this

> ## Tricks for working with file extensions {.callout}
> Working with file extensions can be tough sometimes. Here are a couple examples that demonstrate how to retrieve various parts of a filename.
>
> ```{.bash}
> FILE="example.tar.gz"
> echo "${FILE%%.*}"
> example
> echo "${FILE%.*}"
> example.tar
> echo "${FILE#*.}"
> tar.gz
> echo "${FILE##*.}"
> gz
> ```
