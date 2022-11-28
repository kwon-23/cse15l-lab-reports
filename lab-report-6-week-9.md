# Lab Report 6 Week 9: Grading Scripts

Here is my grade.S bash script along with three tests that I did with three different repositories.

![image](grade.JPG?raw=true)

![image](test1.JPG?raw=true)

![image](test2.JPG?raw=true)

![image](test3.JPG?raw=true)

The example I chose to trace my bash script was the third example, which was the code with the missing semicolon, which would result in a compiler error, 
whichwould be shown by my bash script and tests. The first two lines of my bash script set the e flag, which allows the script to stop once it reaches one 
error, and the second line sets the CPATH to ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar", which is primarily used to make it easier to type out the 
compiler commands later. These two lines do not have any standard error nor standard output, and the return codes were both 0. The next line removes any 
existing directories named "student-submission", and similarly to the previous lines it has no standard error nor standard output and has a return code of 0. 
The next line is the git clone command, which clones the files from the repository into the local directory. The standard output for this command is the 
"Cloning into student-submission...", and does not have a standard error. The return code if the clone is successful is 0. My bash script clones the 
repository in the URL to the local repository. The next line is to get into the copied repository with cd. This has no standard error nor output and has a 
return code of 0. The if statement of the next line checks to see if the required file, ListExamples.java, exists with the -f command. The if statement has a 
! to return true if the find statement does not find the files. Because the file exists in the repository that I am using, the if statement returns false. 
After the if statement, the next two lines copy ListExamples.java from the directory to the directory right outside it, then also changes the working 
directory to the one right outside it with cd. Both commands do not have a standard error or output, and the return code is once again 0. The next line sets 
+e, which makes it so that the code will continue to run even though a bug may be found in order to complete all of the tests. This line does not have a 
standard error or output and its return code is 0. The next line compiles the code, and because the code I used for the example has a compiler error, this 
has a standard error of the compiler error message, which can be seen below:

```
ListExamples.java:15: error: ';' expected
        result.add(0, s)
                        ^
1 error
```

After this, the return code is set to 1. The next line is an if statement that checks to see if the return code is still 0. If the code is still 0, the if
statement returns false, and nothing happens. However, because the return code is not 0 since the compilation of the code failed, the standard output is
"Compilation of the code failed.", and the bash script exits. There is no standard error for those lines. 
