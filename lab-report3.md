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

3. Another usage of the `find` command can come from combining it with the `-exec` flag, this allows you to pass through other commands that run on files you have found with your `find` command.

- For example, we could run `find ./technical -name "chapter*.txt" -exec wc {} \;` would print out:
```
 731  19260 119387 ./technical/911report/chapter-1.txt
  603  6064 47910 ./technical/911report/chapter-10.txt
  817  9414 71968 ./technical/911report/chapter-11.txt
  1539  15623 129126 ./technical/911report/chapter-12.txt
 1089 10689 90943 ./technical/911report/chapter-13.1.txt
  1236  14348 111804 ./technical/911report/chapter-13.2.txt
  1718  19349 152185 ./technical/911report/chapter-13.3.txt
  2941  34343 268853 ./technical/911report/chapter-13.4.txt
  3237  37985 294230 ./technical/911report/chapter-13.5.txt
  948 10539 80751 ./technical/911report/chapter-2.txt
  3159  33834 267519 ./technical/911report/chapter-3.txt
  1204  13004 100212 ./technical/911report/chapter-5.txt
  1898  19381 150961 ./technical/911report/chapter-6.txt
  1579  17276 129949 ./technical/911report/chapter-7.txt
 1036 11324 85871 ./technical/911report/chapter-8.txt
  1885  19748 151529 ./technical/911report/chapter-9.txt
```
- There's two important things to note about the syntax of the `-exec` flag, first is that in order to pass through the files found by `find` as the parameter to the new command, we must use `{}` as the parameter to that command.
- Second, in order to end exec and run the command, we must end the line with a space followed by `\;`, without the space it will not recognize this as the end of the command.

- Using the command in this way could be useful because it allows you to save time by not having to find a file directory then run a different command on that directory manually. Additionally, it makes it easier to understand the information since everything is printed into one block rather than separated by multiple commands.

4.
