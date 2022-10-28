# Lab Report 3 Week 3: Search Engine and Bugs

Part One: Search Engine
-----------------------

Here is the code for my SearchEngine.java file for the search engine:

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.List;

class Handler implements URLHandler {
    private List<String> words = new ArrayList<>();
    private List<String> matchWords = new ArrayList<>();

    public String handleRequest(URI url){  
        if (url.getPath().equals("/")) {
            if (words.size() == 0){
                return String.format("Enter some words with /add?s=");
            }
            else {
                return String.format("Enter something to search with /search?s=.");
            }
        }
        else {
            System.out.println("Path: "+ url.getPath());
            if(url.getPath().contains("/add")){
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    words.add(parameters[1]);
                    return String.format("%s", parameters[1]);
                }
            }
            else if(url.getPath().contains("/search")){
                String[] parameters = url.getQuery().split("=");
                if(parameters[0].equals("s")) {
                    for(int x = 0; x < words.size(); x++){
                        if((words.get(x)).contains((parameters[1])) == true){
                            matchWords.add(words.get(x));
                        }
                    }
                    String result = "";
                    for(int y = 0; y < matchWords.size(); y++){
                        result += matchWords.get(y) + " ";
                    }
                    matchWords.clear();
                    return String.format("%s", result);
                }
            }
            else if(url.getPath().contains("/size")){
                return String.format("%d", words.size());
            }
            return "404 Not Found";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number");
            return;
        }

        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```

When I first run the code and open the link to the localhost, the website looks like this:

![image](start.jpg?raw=true)

Here, the list words is empty, along with the matchWords list. The main method is called here, and the main method creates a new Handler object that is 
run with the Server class, which starts my website.

To add a word, you need to append /add?s= and the word to the end of the URL, and the word should be printed out on the website.

![image](add_string.JPG?raw=true)

By adding /add?s=string to the URL, the method handleRequest is called, and it goes to the nested if-else statements, where the array **parameters** first
takes in the letter s, which tells the loop that there is a string to add. After this, **parameters[1]**, which holds the word string, is added to the
List **words**, and because there is no specified index, it is added at the end of the List. The program then exits the method, as it is finished. The main
change is that now there is a word, string, in the **words** list.

![image](add_bazinga.JPG?raw=true)

Adding another word bazinga goes through the same process as before, but with a different word in **parameters[1]**. 

To search for the words in the list words that contain a specific word or phrase, you need to append /search?s= and the word or phrase to search for at
the end of the URL, and the words containing that word/phrase should be printed out.

![image](search.JPG?raw=true)

Here, the method handleRequest is called, and once again goes into the nested if-else statements, where the array **parameters** first takes in the letter
s for the string input. Then, the method goes through the **words** list searching for any string that contains the string in **parameters[1]**, which was 
the string given to the URL. For each string that does contain the specified word/phrase, the code, through a for loop, adds the word from the **words** 
list to another list, **matchWords**, which, once finished running, goes to another for loop that adds all the strings in **matchWords** into a string, 
**result**, which stores all of the words separated by a space. Finally, the matchWords list is cleared for future use, and the string **result** is printed
out to the website.


Part Two: Bugs
--------------

The first bug is in the file ArrayExamples.java. The first method, **reverseInPlace**, has the code

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

and has the purpose of reversing an array. However, this code is buggy, and does not function properly.

When given the input array **[1,2,3,4]**, the symptom, or the failed output, will be **[4,3,3,4]**. This is due to the code being incorrect, as in order
to reverse an array, the values in the respective spots must be swapped. The code only replaces the values at the start with the values at the end, so when
it comes to copying the values **1 and 2** at the end of the array, the only values to copy from are **3 and 4**. In order to fix this, you need to do two 
swaps each, having a placeholder to hold a value while the other value is copied over it, and instead of traversing through the entire array, only go through half. The fixed code should look like this:

```
static void reverseInPlace(int[] arr) {
    int placeholder = 0;
    for(int i = 0; i < arr.length/2; i += 1) {
        placeholder = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = placeholder;
    }
}
```


The second bug I chose is in the file ListExamples.java. The first method, **filter**, has the code

```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
```

and has the purpose of returning a new list that has all the elements for which StringChecker, which checks if a certain value is a string, returns true. The
values are returned in the same order as in the input list. However, due to a bug, this method does not function properly.

With the input list **["a", "b", "c", "d"]**, the expected output would be the same list, **["a", "b", "c", "d"]**, but instead the list **["d", "c", "b", "a"]** is returned. This is due to an error in the code, as the **add()** function has the value and an int for an index as a parameter. Because the 0 as a parameter tells the function to add the string at the beginning of the list instead of at the end. Due to this, the list returned is in reverse order. In order to fix this, all that needs to be done is to remove the parameter 0, which calls a different overloaded function that automatically puts the input at the end of the list. The fixed code should look like this:

```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
```
