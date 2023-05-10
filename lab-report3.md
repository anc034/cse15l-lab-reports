# **CSE 15L Lab Report 3**

## Part 1 - Interesting Command Applications

- For this lab report we'll be looking at the `find` command and looking at 4 interesting ways you can use it in the command line.
- We will see how each command is useful and what it can be used for and we will show examples by using it on files and directories from the `/technical` directory from Lab 4.

1. The first interesting usage we will look at is the `-maxdepth` modifier for the `find` command. This modifier followed by a number limits the amount of directories `find` travels through dependent on the number you provide.
- For example, `find *args* -maxdepth 2` would only travel through two directories at most.|

- Now, if we look at our `/technical` directory and run the command `find ./technical -maxdepth 1` we find the output to be this:
```
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/plos
```
- However, if this command was run without the modifier such as `find ./technical` we would see that the output is very different.:
```
........
./technical/plos/pmed.0020246.txt
./technical/plos/pmed.0020247.txt
./technical/plos/pmed.0020249.txt
./technical/plos/pmed.0020257.txt
./technical/plos/pmed.0020258.txt
./technical/plos/pmed.0020268.txt
./technical/plos/pmed.0020272.txt
./technical/plos/pmed.0020273.txt
./technical/plos/pmed.0020274.txt
./technical/plos/pmed.0020275.txt
./technical/plos/pmed.0020278.txt
./technical/plos/pmed.0020281.txt
```
- For the sake of space, the ``..........`` denotes all the files preceding the ones shown in the code block, but the idea is that when there is no maximum depth, the find command finds every possible file in the given directory and the directories in that directory and so on. However when given a maximum depth with the modifier you can limit the amount of directories the command can access

- An important note about this modifier is that it **must** come before any other flags, for example you cannot do `find ./technical -name "*.txt" -maxdepth 1` instead you must format it as `find ./technica; -maxdepth 1 -name "*.txt"`.
- If formatted in the incorrect order you will receive this error:
```
find: warning: you have specified the global option -maxdepth after the argument -name, but global options are not positional, 
i.e., -maxdepth affects tests specified before it as well as those specified after it.  Please specify global options before other arguments.
```
- This can be useful if you want to reduce the amount of directories and file names you're given as shown above. It can also be useful if you specifically want to know if there's something inside of the specified directory rather than in a subfolder of that directory.

2. Another usage of the `maxdepth` modifier is that if paired with modifiers such as `-f` you can use it to know if a directory contains any files or if it only contains directories.
- For example, if we take the command from the first example:  `find ./technical -maxdepth 1`, we see that it returned a set of directories.
- However, if we were interested in learning if there were any files in this directory but didn't want to spend time reading the file names, we could run something like `find ./technical -maxdepth 1 -type f`:
```
$ find ./technical -maxdepth 1 -type f

```
- Notice that there is nothing below the command, this is because there are no files in the given directory meaning that the command will not print anything.
- By using this flag in combination with the maxdepth modifier, we have cut down the amount of time someone would need to spend looking at this to determine if there are any files or not, this could be very useful in cases where there are hundreds of directories in the given directory.

- Lastly, both of these examples were obtained from [here](https://www.redhat.com/sysadmin/linux-find-command) and I found it by searching for interesing usages for the find command on google.
