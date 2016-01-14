# covered topics by swc

##00-intro
+ what is bash

##01-filedir
+ whoami  
+ pwd  
+ file system overview
+ ls (-F, -a, arguments) -- cut some here
+ cd (cd ..)
+ tab completion
+ meaning of ~

##02-create

reorganize these
+ mkdir
+ nano text editor (vi instead?)
+ rm (doesn't work on directories, files gone forever)
+ rmdir
+ rm -r
+ mv for renaming, moving
+ cp
get rid of challenge problems at end and replace with something more relevant

##03-pipefilter

+ wildcards
+ wc (-w, -l, -c)
+ ">"
+ cat
+ sort (-n, add uniq?)
+ head, tail
+ "|"
+ "<" redirects input
+ ">>"

skim down examples, some are good

##04-loop

maybe introduce shell scripting first

introduce shell variables first with echo?
+ basic for loops, shell variables
+ concatenation with shell variables
+ echo as a debugging tools

##05-script

+ they are running scripts with "bash" first
+ shell script arguments
+ use quotes to make things robust vs. spaces
+ comments
+ $@ - all arguments

script reading comprehension examples are great
need to cover permissions!

##06-find

+ grep example is hilarious
+ grep examples are great
+ man
+ find lessons are good
+ shell expansion of *
+ $(command)

##stuff not covered that should be covered
+ less/more
+ permissions/chmod/sudo
+ wget
+ file parsing
+ #! in scripts
+ unzipping files
+ awk/sed?
+ logfile creation
