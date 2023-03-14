# Lab Report 3
## Researching Commands (find)

### find -name

The -name option is used with the find command to search for files or directories with a specific name or pattern. You can use a wildcard such as * to specify part of the name or pattern you want to match. For example, \*.txt would match all files with a ".txt" extension. When using -name, you must enclose the pattern in quotes to prevent the shell from expanding the pattern before passing it to find.

In this example, we find everything in the `written2` directory that start with a capital C. Notice that there is no -r option attached but the find command automatically searchs recursively in all directories.

```
[cs15lwi23avy@ieng6-203]:written_2:561$ find . -name "C*"
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Castro
./travel_guides/berlitz2/California-History.txt
./travel_guides/berlitz2/California-WhatToDo.txt
./travel_guides/berlitz2/California-WhereToGo.txt
./travel_guides/berlitz2/Canada-History.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/CanaryIslands-History.txt
./travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
./travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
./travel_guides/berlitz2/Cancun-History.txt
./travel_guides/berlitz2/Cancun-WhatToDo.txt
./travel_guides/berlitz2/Cancun-WhereToGo.txt
./travel_guides/berlitz2/China-History.txt
./travel_guides/berlitz2/China-WhatToDo.txt
./travel_guides/berlitz2/China-WhereToGo.txt
./travel_guides/berlitz2/Costa-History.txt
./travel_guides/berlitz2/Costa-WhatToDo.txt
./travel_guides/berlitz2/Costa-WhereToGo.txt
./travel_guides/berlitz2/CostaBlanca-History.txt
./travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
./travel_guides/berlitz2/Crete-History.txt
./travel_guides/berlitz2/Crete-WhatToDo.txt
./travel_guides/berlitz2/Crete-WhereToGo.txt
./travel_guides/berlitz2/CstaBlanca-WhereToGo.txt
./travel_guides/berlitz2/Cuba-History.txt
./travel_guides/berlitz2/Cuba-WhatToDo.txt
./travel_guides/berlitz2/Cuba-WhereToGo.txt
```

That's a lot of files. Let's say that we only need the files and directories that begin with a capital C and are from the subdirectory `./non-fiction/OUP/`. We can edit the command so that it looks like the following.

```
[cs15lwi23avy@ieng6-203]:written_2:562$ find ./non-fiction/OUP/ -name "C*"
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Castro
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompt I provided was 'find command options'. After that, a bit of experimentation led me to the examples shown above.

### find -type

The -type option takes a single argument that specifies the type of file to search for. This can include `d` for directories, `f` for files, `l` for links and so on. 

Building on the previous example, let's that now we are only interested in regular files that have a title that begins with capital C, and are in the subdirectory `./non-fiction/OUP/`. We can use the following command.

```
[cs15lwi23avy@ieng6-203]:written_2:563$ find ./non-fiction/OUP/ -name "C*" -type f
./non-fiction/OUP/Berk/CH4.txt
```

Now, let's say we are interested in the structure of the file system, and only want to know about all the directories. We can use the following command:

```
[cs15lwi23avy@ieng6-203]:written_2:564$ find . -type d
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Berk
./non-fiction/OUP/Castro
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Rybczynski
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```

The information on this was also provided with ChatGPT, alongside personal experimentation. The prompt I provided was 'can you gib a short description of the -type option in find plz bruv'

### find -size

The -size option is used with the find command to search for files based on whether they are smaller or larger than the specified size. It allows you to give a size in bytes, kilobytes, megabytes, or gigabytes.

For example, let us say we want to find all small regular files - files that take less than 2 kilobytes of spaces. We can use the command as follows. Note that the `-2k` does not represent a new option, but is rather a parameter for `-size`. The `-` in this does not represent a new option, but rather the idea of 'less than' 2 kilobytes.

```
[cs15lwi23avy@ieng6-203]:written_2:586$ find . -type f -size -2k
./travel_guides/berlitz1/HandRIbiza.txt
./travel_guides/berlitz1/HandRIstanbul.txt
```

Now, let us say we want to find all large txt regular files - since txt files are usually small, a txt file of 200 kilobytes and above can be considered large. We can use the following command. Note that, as `-2k` was a parameter, we have replaced the `-2k` with a `+200k` to symbolize greater than 200 kilobytes.

```
[cs15lwi23avy@ieng6-203]:written_2:589$ find . -type f -name "*.txt" -size +200k
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
```

The information on this command was provided by ChatGPT, along with more personal experimentation. The command prompt used was 'give some useful examples of using the find command with options'.

### find -delete

When the `-delete` command is called, it deletes all files and directories that match the search criteria specified by the find command.

Let's say that our computer is low on memory, and we could really use a few hundred kilobytes for a different type of data. Building on the previous examples, we can delete the txt regular files that are above 200kb to free up some space. This is shown in the following example.

Please note the use of the `find` command before the `-delete` option is added. This is because the `-delete` option is quite a dangerous command, as it does not prompt the user for confirmation before deleting files. It's a good idea to test your the command without the -delete option first, to ensure that the correct files and directories will be deleted. Backups are also a good idea, in case you mess up.

```
[cs15lwi23avy@ieng6-203]:written_2:590$ find . -type f -name "*.txt" -size +200k
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
[cs15lwi23avy@ieng6-203]:written_2:590$ find . -type f -name "*.txt" -size +200k -delete
[cs15lwi23avy@ieng6-203]:written_2:591$ find . -type f -name "*.txt" -size +200k
[cs15lwi23avy@ieng6-203]:written_2:592$
```

Now, let us say that we want to clean up our file structure by deleting some empty directories. We can do this by adding the `-empty` modifier alongside the `-delete` command. As `written2` does not contain any empty directories, we can create some to demonstrate the effect it would have.

Please note that 3 directories were created - the `hello` directory, a directory inside this new directory called `hellohello`, and a directory inside `./travel_guides` called `helloTravel`. This means that the `hello` directory is not empty - it contains the `hellohello` empty directory. However, it is also deleted when the `-delete` command is called. This further demonstrates the unpredictability of the `-delete` option - it deleted directories that weren't shown with the `find` command without the `-delete` option. 

```
[cs15lwi23avy@ieng6-203]:written_2:606$ mkdir hello
[cs15lwi23avy@ieng6-203]:written_2:607$ mkdir ./hello/hellohello
[cs15lwi23avy@ieng6-203]:written_2:608$ mkdir ./travel_guides/helloTravel
[cs15lwi23avy@ieng6-203]:written_2:609$ find . -type d -empty
./travel_guides/helloTravel
./hello/hellohello
[cs15lwi23avy@ieng6-203]:written_2:610$ find . -type d -empty -delete
[cs15lwi23avy@ieng6-203]:written_2:611$ find . -type d -empty
[cs15lwi23avy@ieng6-203]:written_2:612$ ls
non-fiction  travel_guides
```

The idea of this command was provided by ChatGPT, but was fleshed out with more personal experimentation. The command prompt used was 'give some useful examples of using the find command with options'.
