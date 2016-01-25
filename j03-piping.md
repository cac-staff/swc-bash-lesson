---
layout: page
title: The Unix Shell
subtitle: Wildcards and Piping
minutes: 15
---

> ## Learning Objectives {.objectives}
>
> *   Redirect a command's output to a file.
> *   Process a file instead of keyboard input using redirection.
> *   Construct command pipelines with two or more stages.
> *   Explain what usually happens if a program or pipeline isn't given any input to process.

Now that we know most of the basic UNIX commands, we are going to explore some more advanced features. The first of these features is the wildcard `*`. In our examples before, we've done things to files one at a time and otherwise had to specify things explicitly. The `*` character lets us speed things up and do things across multiple files.

Ever wanted to move, delete, or just do "something" to all files of a certain type in a directory? `*` lets you do that, by taking the place of one or more characters in a piece of text. So `*.txt` would be equivalent to all .txt files in a directory for instance. `*` by itself means all files. Let's use some example data to see what I mean.

TODO get example data hosted somewhere

```{.bash}
wget <NEED LINK>.wildcard_example.tar.gz
tar -xzf wildcard_example.tar.gz
ls
```
```{.output}
 dmel_unique_protein_isoforms_fb_2016_01.tsv  SRR307026_2.fastq
 Drosophila_melanogaster.BDGP5.77.gtf         SRR307027_1.fastq
 fb_synonym_fb_2016_01.tsv                    SRR307027_2.fastq
 gene_association.fb                          SRR307028_1.fastq
 SRR307023_1.fastq                            SRR307028_2.fastq
 SRR307023_2.fastq                            SRR307029_1.fastq
 SRR307024_1.fastq                            SRR307029_2.fastq
 SRR307024_2.fastq                            SRR307030_1.fastq
 SRR307025_1.fastq                            SRR307030_2.fastq
 SRR307025_2.fastq                            wildcard_examples.tar.gz
 SRR307026_1.fastq
```

Now we have a whole bunch of example files in our directory. For this example we are going to learn a new command that tells us how long a file is: `wc`. `wc -l <file>` tells us the length of a file in lines.

```{.bash}
wc -l Drosophila_melanogaster.BDGP5.77.gtf
```
```{.output}
471308
```

 Interesting, there are 471308 lines in our `Drosophila_melanogaster.BDGP5.77.gtf` file. What if we wanted to run `wc -l` on every .fastq file? This is where `*` comes in really handy.

```{.bash}
wc -l *.fastq
```
```{.output}
 20000 SRR307023_1.fastq
 20000 SRR307023_2.fastq
 20000 SRR307024_1.fastq
 20000 SRR307024_2.fastq
 20000 SRR307025_1.fastq
 20000 SRR307025_2.fastq
 20000 SRR307026_1.fastq
 20000 SRR307026_2.fastq
 20000 SRR307027_1.fastq
 20000 SRR307027_2.fastq
 20000 SRR307028_1.fastq
 20000 SRR307028_2.fastq
 20000 SRR307029_1.fastq
 20000 SRR307029_2.fastq
 20000 SRR307030_1.fastq
 20000 SRR307030_2.fastq
320000 total
```

 That was easy. What if we wanted to do the same command, except on every file in the directory? A nice trick to keep in mind is that `*` by itself matches *every* file.

```{.bash}
wc -l *
```
```{.output}
 22129 dmel_unique_protein_isoforms_fb_2016_01.tsv
471308 Drosophila_melanogaster.BDGP5.77.gtf
1304914 fb_synonym_fb_2016_01.tsv
106290 gene_association.fb
 20000 SRR307023_1.fastq
 20000 SRR307023_2.fastq
 20000 SRR307024_1.fastq
 20000 SRR307024_2.fastq
 20000 SRR307025_1.fastq
 20000 SRR307025_2.fastq
 20000 SRR307026_1.fastq
 20000 SRR307026_2.fastq
 20000 SRR307027_1.fastq
 20000 SRR307027_2.fastq
 20000 SRR307028_1.fastq
 20000 SRR307028_2.fastq
 20000 SRR307029_1.fastq
 20000 SRR307029_2.fastq
 20000 SRR307030_1.fastq
 20000 SRR307030_2.fastq
2317119 total
```

> ## Multiple wildcards {.challenge}
> You can even use multiple `*`s at a time. How would you run `wc -l` on every file with "fb" in it?

> ## Using other commands {.challenge}
> Now let's try cleaning up our working directory a bit. Create a folder called "fastq" and move all of our .fastq files there.

---------------------------------

## Piping output

Each of the commands we've used so far does only a very small amount of stuff. However, it's extremely easy to chain UNIX commands together in new and awesome ways.
