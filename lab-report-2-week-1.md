# Lab Report 2 Week 1: ieng6 Tutorial

Installing VScode
-----------------

In order to download VScode, all you have to do is go to https://code.visualstudio.com/ and click the button on the site that says "Download for Windows". The download should automatically start, and once it finishes, just open the downloaded file and follow the steps that are given to you to finish the installation process. 

![image](vscode.JPG?raw=true)

Remotely Connecting
-------------------

Remotely connecting to the ieng6 server is done through the ssh command, which stands for secure shell. In order to remotely connect to the ieng6 server, you need to type the command **ssh cs15lfa22__@ieng6.ucsd.edu**, where the space is for your personal two letter code. This command not only works for CSE 15L, as other classes can use this command by changing the class name and the quarter name.

![image](ieng6_login.JPG?raw=true)

When doing the command, it will ask for your password, which you will have to reset using the global password reset system. Once you reset your password, you can login to the remote server. Remember that whenever you type in your password, there are no visible signs that you are typing the password in, so make sure you get it right.

Trying Some Commands
--------------------

Within the remote server, there are several different commands that you can try, such as but not limited to **cd**, **ls**, **cp**, and **cat**. The **cd** command is primarily used to go to a certain directory, and using **cd** without any specific directory leads to the directory right outside the one that you are currently in. The command **ls** is used to display all the files in your current directory. The command **cp** is used to copy certain files to different locations, and the command **cat** is used to concatenate and print the files that you want.

![image](commands.JPG?raw=true)

Moving Files with scp
---------------------

You can easily move files between the remote server and your personal device through the command **scp**. For this example, we have a file WhereAmI.java that we can move from my personal device to the remote server. The command is **scp file_name user_to_move_to:directory_to_move_to**, so to move our WhereAmI.java file to the remote server, the command is **scp WhereAmI.java cs15lfa22oy@ieng6.ucsd.edu:~/**. Doing so will prompt you for the password, and then your files will be copied onto the remote server.

![image](scp.JPG?raw=true)

Setting an SSH Key
------------------

