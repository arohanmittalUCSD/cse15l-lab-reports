# Lab Report 3
## Researching Commands (grep)

### grep -r

The grep command searches for the pattern in the specified files, but does not search recursively through directories. If you specify multiple files, grep will search each file separately and print out any matching lines.

The grep -r command, on the other hand, searches for the pattern recursively through all files and directories under a given directory. This means that it will search through all files in subdirectories as well, and print out any matching lines along with the name of the file and the line number.

We can see here, that without having to specify a file name, we were able to find the occurrence of "multiple texttile channels" in the given directory.
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

It is worth noting in this example that the results include words that consist of the given word. For example, here, "Othello" contains the word "hello", and is therefore shown too.
```
[cs15lwi23avy@ieng6-203]:written_2:167$ grep -r "hello"           
travel_guides/berlitz1/WhereToHongKong.txt:        the local people smile “hello” and, if you’re lucky, point you to a
travel_guides/berlitz1/WhereToItaly.txt:        (or Ca’ Grande), while gondoliers claim Othello’s Desdemona lived in
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompt I provided was 'grep vs grep -r'

### grep -c

grep -c can be used to count the number of occurrences of a specific word in a log file, the number of times a certain error message appears in a log file, the number of lines in a file that match a certain regular expression, the number of times a specific user appears in a system log file, and any other scenario in which you want to count the number of occurences of something in a file.

Here, the command counts the number of times "textile" appears in ch2.text lines
```
[cs15lwi23avy@ieng6-203]:written_2:169$ grep -c "textile" non-fiction/OUP/Abernathy/ch2.txt 
26
```

Here, we count the total number of times the word "textile" appears in the current directory. grep -r -c displays the count for each file seaparately, so we have a small program to the side which can use that result and give us our total number.
```
[cs15lwi23avy@ieng6-203]:written_2:171$ grep -r -c "textile" | awk -F: '{total += $2} END {print total}'
126
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompts I provided were 'gimme some egs of when you can use grep -c i dun wanna think plz' and 'using grep -c to give total count of occurrences of a word in a directory'.

### grep -w

This command filters the results so that only whole word results appear. This means that our previous result containing "Othello" has been removed, as it is not wholely "hello".
```
[cs15lwi23avy@ieng6-203]:written_2:173$ grep -r -w  "hello"
travel_guides/berlitz1/WhereToHongKong.txt:        the local people smile “hello” and, if you’re lucky, point you to a
```

This even works with the counter - results such as "textiles" (not the same as "textile"), have been removed so that the total count is brought down from 126 to 88.
```
[cs15lwi23avy@ieng6-203]:written_2:174$ grep -w -r -c "textile" | awk -F: '{total += $2} END {print total}'
88
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompt I provided was 'what are all the command line options for the grep command-line utility'

### grep -m NUM

This command limits search results so that only the given NUM matches are shown from a file.

It's worth noting that, in this example, textile shows up twice in the first result and once in the second result. This is because the grep command focuses exclusively on counting lines, not occurrences.

```
[cs15lwi23avy@ieng6-203]:written_2:178$ grep -m 2 "textile" non-fiction/OUP/Abernathy/ch2.txt 
The emergence of textile, apparel, and retail enterprises in the United States is full of fascinating twists. In 1790, for instance,
an act of industrial espionage is said to have launched the domestic textile industry, if not American manufacturing in general. At
that time, Samuel Slater, a skilled mechanic, built the first successful water-powered yarn spinning mill in Pawtucket, Rhode Island.
Yarn was in short supply in the new country and much in demand in households that did hand weaving as well as in workplaces with 
looms that produced sheeting, shirting, and stockings for commerce. Some of the American states and improvement societies had even 
offered generous rewards for the establishment of water-powered combing and spinning, especially those based on state-of-the-art 
English Arkwright operations. But British law strictly prohibited the export of drawings, plans, or models of these new technologies. 
It took somebody like Slater—an indentured apprentice for over six years at the Arkwright and Strut’s plant in Milford, England—to 
ferry the plans to America.1
The Slater mill not only copied British technology but recreated that country’s arrangement of family labor, which included young 
children, six-day weeks, the minimum twelve-hour day, Sabbath schools, and payment of wages partly in goods and partly in cash. The 
form of ownership and management also followed British lines—one partner financed the venture, while the other furnished the 
technical know-how. For these accomplishments, Samuel Slater has been called “the father of American manufactures.” His story 
underscores the international role of textiles and apparel, their impetus in national economic development, and their place in 
conflicts over domestic production and imports—a theme that recurs throughout U.S. history. For example, from the outset of the new 
nation, President George Washington and his Secretary of the Treasury Alexander Hamilton wanted to encourage U.S.-based industry. 
Indeed, Washington wore a dark brown suit, entirely made in America, for his first inaugural on April 30, 1789.3
```

In this example, notice that the command finds 1 example from each file rather than 1 example total.
```
[cs15lwi23avy@ieng6-203]:written_2:180$ grep -r -m 1 "hello"
travel_guides/berlitz1/WhereToHongKong.txt:        the local people smile “hello” and, if you’re lucky, point you to a
travel_guides/berlitz1/WhereToItaly.txt:        (or Ca’ Grande), while gondoliers claim Othello’s Desdemona lived in
```

The information on this command was provided graciously by our Lord and Saviour ChatGPT. I support Skynet. The prompt I provided was 'what are all the command line options for the grep command-line utility'
