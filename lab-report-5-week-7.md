# Lab Report 5 Week 7: Vim and Beyond CSE15L

Part 1: Vim
-----------

The task I chose to do was to replace each instance of the variable start to base in the getFiles function of DocSearch. In order to do this, I will be using
the commands below:

```
/start<Enter>cebase<Esc>n.n.:w<Enter>
```

The first command once you open the file is `/start<Enter>`, which puts the cursor at the first instance of start.
  
![image](start_enter.JPG?raw=true)
  
The next commands, `cebase<Escape>`, are commands that perform two steps. The first, `ce`, make it so that the vim editor changes up to the end of the given 
word and puts the user in insert mode. After, since the initial variable start is deleted, you can write in the new variable name, `base`. The escape key is 
pressed at the end to escape out of insert mode.
  
![image](cebase.JPG?raw=true)
  
The next commands, `n.n.`, are used to go to the next instance of the original word - start - using `n` and do the same command that was done to the first start
with the command `.`. This is repeated again to change the next and last start to base.

![image](n1.JPG?raw=true)

![image](n2.JPG?raw=true)


Part 2: Beyond CSE15L
---------------------

When making very small edits, like changing a variable name or adding a test, the first method took me about a minute to do, while doing the change on the ssh session through vim took me around only 30 seconds, which was a lot less time. This might be because I already am very used to using vim to edit and run code, while I think that doing scp and copying from Visual Studio might take longer for me as I am not as comfortable.

Q1: If I were to edit code that I had to run remotely on the ieng6 server, I would much prefer using Vim, as I am more comfortable making changes and running on the ieng6 servers and scping the files back to my local machine to turn into Gradescope. 
Q2: I think the main thing that would make me use my local machine over the remote is when I want to use a different environment, as the remote server only has vim while my local machine can use a variety of different code editors that may help the coding process.
