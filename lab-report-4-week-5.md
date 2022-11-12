# Lab Report 4 Week 5: Researching Commands

For this lab report, I chose to learn more about the command **grep**. The **grep** command is used to search for certain strings within given files, and the commands for **grep** in the terminal follow this format:

```
grep [OPTIONS] PATTERN [FILE(S)]
```

If the pattern consists of more than one word, then you need to put the entire phrase into single quotes in order for the entire phrase to be searched for. In order to have multiple command line options, you can just add the letter of the option to the end of the other option you already have (so if you were to use the options **-r** and **-w**, you would type **-rw**).

Command Line Option 1: -r
-------------------------

The command line option **-r** allows **grep** to search recursively for all files under each directory. This means that **grep** goes through the subfolders of the given directory and searches all the files for the pattern that was given. The **-r** option is incredibly useful as it allows for the user to search through a lot of different files across different directories without having to list out all the individual files for **grep** (as normally, you would need to write out the file names that **grep** searches through).

For example, I searched for the phrase 'incorporation of a', 'having a high, and 'reading a' in all of the files in /docsearch/technical by using the **-r** option. 

![image](incorp.JPG?raw=true)

![image](high.JPG?raw=true)

![image](reading.JPG?raw=true)


Command Line Option 2: -w
-------------------------

In the examples of the usage of **-r**, there were some phrases that were part of a larger phrase instead of being an exact match for the words or phrases that I searched for (like 'spreading assay' showing up as a match when searching for 'reading a'). In order to prevent this and search exclusively for the words or phrases that are not part of a larger word or phrase, you can use the command line option **-w**, which limits the search to exact matches only. This is also useful because it allows for the user to search for only exact matches, as **grep** without the **-w** option can lead to some unwanted matches.

For my examples, I did the phrases 'incorporation of a', 'having a high', and 'reading a' again with the **-w** option, but this time added the **-r** option as well, which led to far less matches, as **grep** only found the exact matches for the search phrases.

![image](wincorp.JPG?raw=true)

![image](whaving.JPG?raw=true)

![image](wreading.JPG?raw=true)


Command Line Option 3: -l
-------------------------

When running **grep**, the output was the file names with the line with the match of the phrase that I searched for. In order to just see the names of the files with the matching phrase, you can use the command line option **-l**, which suppresses the output of the matched lines. This can be useful if the user is only looking for the files with the matches in a cleaner list with only the file names.

For my examples, I searched for the same phrases as before(only the exact matches), and added the **-l** option to see only the file names that contained the phrases.

![image](lincorp.JPG?raw=true)

![image](lhaving.JPG?raw=true)

![image](lreading.JPG?raw=true)
