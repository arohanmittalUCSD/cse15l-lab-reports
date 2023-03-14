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

The -type option is used with the find command to search for files of a specific type. It takes a single argument that specifies the type of file to search for.

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


