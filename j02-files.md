---
layout: page
title: The Unix Shell
subtitle: Writing and reading files
minutes: 30
---

Now that we know how to move around and look at things, let's learn how to read, write, and handle files!

```{.bash}
cd ~
```

What if we want to make a file? There are a few ways of doing this, the easiest of which is simply using a text editor. For this lesson, we are going to us `nano`, since it's super easy to use.

To use `nano` on a file, simply type `nano <filename>`. If the file does not exist, it will be created. `^O` (ctrl + O) saves the file, and `^X` quits. If you have not saved your file upon trying to quit, it will ask you if you want to save.

> ## Using `vi` as a text editor {.callout}
> Although `vi` isn't the easiest or most user-friendly of text editors, you'll be able to find it on any system and it will take you far.
>
> A few things about using `vi` before we start. There are couple modes, a command mode (for doing big operations) and an "insert" mode. You can switch to insert mode with the `i` key, and command mode with `Esc`.
>
> In insert mode, you can type more or less normally. In command mode there are a few commands you should be aware of:
> `:q!` - quit, without saving
> `:wq` - save and quit
> `dd` - cut/delete a line
> `y` - paste a line

Let's make a new file now, type whatever you want in it, and save it.
```{.bash}
nano test.txt
```
![Nano in action](fig/nano-screenshot.png)

Do a quick check to confirm our file was created.
```{.bash}
ls
```
```{.output}
test.txt
```

Let's read our file now. There are a few different ways of doing this, the simplest of which is simply reading the entire file with `cat`.

```{.bash}
cat test.txt
```
```{.output}
This is the contents of our test file.
```
Although `cat` may not seem like an intuitive command with which to open files, it stands for "concatenate"- giving it multiple arguments will print out one file followed by the contents of the next, and so on.

```{.bash}
cat test.txt test.txt
```
```{.output}
This is the contents of our test file.
This is the contents of our test file.
```

We've successfully created a file. What about a directory? We've actually done this before, using `mkdir`.
```{.bash}
mkdir files
ls
```

## Moving and copying files

To practice moving files, we will move `test.txt` to that directory with `mv` (move). `mv`'s syntax is relatively simple, and works for both files and directories `mv <file/directory> <path to new location>`

```{.bash}
mv test.txt files
cd files
ls
```
```{.output}
test.txt
```

`test.txt` isn't a very descriptive name. How do we go about changing it?

It turns out that the way to rename files and folders is with `mv` again. Although this may not seem intuitive at first, think of it as moving a file to be stored under a different name. The syntax is quite similar to moving files: `mv <oldName> <newName>`.

```{.bash}
mv test.txt newname.testfile
ls
```
```{.output}
newname.testfile
```

> ## File extensions are arbitrary {.callout}
>
> In the last example, we changed both a file's name and extension at the same time. On UNIX systems, file extensions (like .txt) are arbitrary. A file is a .txt file only because we say it is. Changing the name or extension of the file will *never* change a file's contents, so you are free to rename things as you wish.

What if we want to copy a file, instead of simply renaming or moving it? Use `cp`. This command has to different uses that work in the same way as `mv`:

+ Copy to same directory (new name): `cp <file> <newFilename>`

+ Copy to other directory (same name): `cp <file> <directory>`

Let's try this out.
```{.bash}
cp newname.testfile copy.testfile
ls
cp newname.testfile ..
cd ..
ls
```
```{.output}
newname.testfile copy.testfile
files Documents newname.testfile
```

## Removing files

We've begun to clutter up our workspace with all of the directories and stuff we've been making. Let's learn how to get rid of them.

## Practice problems

Sometimes it's not practical to read an entire file with `cat`- the file might be way too large or take a long time to open. As an example, we are going to look at a large and complex file type used in bioinformatics.
