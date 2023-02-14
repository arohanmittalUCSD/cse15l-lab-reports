# Lab Report 2
## Researching Commands (grep)

### grep -r

The grep command searches for the pattern in the specified files, but does not search recursively through directories. If you specify multiple files, grep will search each file separately and print out any matching lines.

The grep -r command, on the other hand, searches for the pattern recursively through all files and directories under a given directory. This means that it will search through all files in subdirectories as well, and print out any matching lines along with the name of the file and the line number.

```
[cs15lwi23avy@ieng6-203]:skill-demo1-data:162$ grep -r "multiple textile channels" written_2/
written_2/non-fiction/OUP/Abernathy/ch2.txt:Textile firms, however, have been players in multiple supply channels. There are three m
ajor categories of sales outlets for these manufacturers: (1) woven goods and some knit goods destined for clothing, in which materi
als are sold to apparel-makers for fabrication and assembly; (2) home furnishings—such as sheets, bedspreads, towels, and some knit 
goods—in which the textile firm sells directly to retailers; (3) industrial products, from automobile seat covers and rugs to commer
cial fishing nets, in which a textile firm sells materials to a car company or other nonapparel manufacturer. Thus, there are at lea
st three kinds of relations among the industries, and multiple textile channels are on the rise. Although apparel uses dominated tex
tile consumption in the past, by the early 1980s apparel’s share of fiber consumption was only 37 percent; home furnishings was abou
t 38 percent; and industrial textile products consumed over 20 percent.
```

```
[cs15lwi23avy@ieng6-203]:written_2:167$ grep -r "hello"           
travel_guides/berlitz1/WhereToHongKong.txt:        the local people smile “hello” and, if you’re lucky, point you to a
travel_guides/berlitz1/WhereToItaly.txt:        (or Ca’ Grande), while gondoliers claim Othello’s Desdemona lived in
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompt I provided was 'grep vs grep -r'

### grep -c

grep -c can be used to count the number of occurrences of a specific word in a log file, the number of times a certain error message appears in a log file, the number of lines in a file that match a certain regular expression, the number of times a specific user appears in a system log file, and any other scenario in which you want to count the number of occurences of something in a file.

```
[cs15lwi23avy@ieng6-203]:written_2:169$ grep -c "textile" non-fiction/OUP/Abernathy/ch2.txt 
26
[cs15lwi23avy@ieng6-203]:written_2:170$
```
