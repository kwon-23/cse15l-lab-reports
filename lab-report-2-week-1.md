# Lab Report 2 Week 1: ieng6 Tutorial

Installing VScode
-----------------

In order to download VScode, all you have to do is go to https://code.visualstudio.com/ and click the button on the site that says "Download for Windows". The download should automatically start, and once it finishes, just open the downloaded file and follow the steps that are given to you to finish the installation process. 

![image](vscode.JPG?raw=true)

Remotely Connecting
-------------------

Remotely connecting to the ieng6 server is done through the ssh command, which stands for secure shell. To access the terminal on Visual Studio, go to the top toolbar to where it says **Terminal**, then select **New Terminal**. This will open a terminal you can type your commands into. In order to remotely connect to the ieng6 server, you need to type the command **ssh cs15lfa22__@ieng6.ucsd.edu**, where the space is for your personal two letter code. You can find this two letter code from the website [here](https://sdacs.ucsd.edu/~icc/index.php). Type in your username and student ID in order to get your class ID, which contains your two letter code. This command not only works for CSE 15L, as other classes can use this command by changing the class name and the quarter name.

![image](ieng6_login.JPG?raw=true)

When doing the command, it will ask for your password, which you will have to reset using the global password reset system. Once you reset your password, you can login to the remote server. Remember that whenever you type in your password, there are no visible signs that you are typing the password in, so make sure you get it right.

Trying Some Commands
--------------------

Within the remote server, there are several different commands that you can try, such as but not limited to **cd**, **ls**, **cp**, and **cat**. The **cd** command is primarily used to go to a certain directory, and using **cd** without any specific directory leads to the directory right outside the one that you are currently in. The command **ls** is used to display all the files in your current directory. The command **cp** is used to copy certain files to different locations, and the command **cat** is used to concatenate and print the files that you want.

![image](commands.JPG?raw=true)

Moving Files with scp
---------------------

You can easily move files between the remote server and your personal device through the command **scp**. For this example, we have a file WhereAmI.java that we can move from my personal device to the remote server. The code for the file WhereAmI.java can be written as

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

The command is **scp file_name user_to_move_to:directory_to_move_to**, so to move our WhereAmI.java file to the remote server, the command is **scp WhereAmI.java cs15lfa22oy@ieng6.ucsd.edu:~/**. Doing so will prompt you for the password, and then your files will be copied onto the remote server.

![image](scp.JPG?raw=true)

Setting an SSH Key
------------------

SSH keys greatly simplify the process of logging into a remote account by removing the need to type in a password. In order to make an SSH key for your remote account, you have to type in the command **ssh-keygen** on your local device, which will prompt you to enter a file to save the key. Type in the directory **/Users/user_name/.ssh/id_rsa**, and press enter twice to ignore setting a passphrase. Then, log onto your remote server through normal ssh and type the command **mkdir .ssh**, which is where your public key, which you made by the command **ssh-keygen**, will be placed. Log out of the remote server with exit, then type the command **scp /Users/user_name/.ssh/id_rsa/pub cs15lfa22__@ieng6.ucsd.edu:~/.ssh/authorized_keys**, making sure to type in your personal information where user_name and the __ are.This should be the process to be able to log into the remote server without typing in your password. However, I already have a key that I need to use in another class, so it does not work for me.

![image](ssh_keygen.JPG?raw=true)

Optimizing Remote Running
-------------------------

By adding commands in quotes to the end of certain commands like ssh, and using semicolons to run multiple commands in the same line, connecting and using files in the remote server can become a lot easier. For example, in order to locally edit WhereAmI.java, then copying it onto the remote server and running it can be done with two commands. The command **scp WhereAmI.java cs15lfa22__@ieng6.ucsd.edu:/~** is used to copy the edited WhereAmI.java onto the remote server, and the command **ssh cs15lfa22__@ieng6.ucsd.edu “javac WhereAmI.java ; java WhereAmI”** is used to log onto the server and compile and run WhereAMI on the remote server. 

![image](optimized_running.JPG?raw=true)
