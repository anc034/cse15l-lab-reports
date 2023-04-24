# **CSE 15L Lab Report 2**

## Part 1 - String Server
![Image](StringServer.png)

- This screenshot is showing the code for the String Server that we created and are hosing locally. The `handleRequest` method in the `SearchEngine` class deals with checking the URL that the user is inputting in their search engine. 

- The `main` method in the `StringServer` class is what allows us to use the command line to input the port number to start the server in VS Code. In the following screenshots we will see how these two methods allow the user to add strings and see the total list of strings.

![Image](addHello.png) ![Image](addHow.png) ![Image](StringTerminal.png)

- The first two screenshots are showing two separate instances of adding a string to the server and the third screenshot shows the terminal commands necessary to start the server.

- The first two screenshots are each calling the `handleRequest` method and are passing through their specific URL's as the parameter. For the first screenshot it would be `localhost:4123/add-message?s=Hello` and for the second screenshot it would be `localhost:4123/add-message?s=How%20are%20you` (An important note is that the URL seems to add "%20" when there is a space in the string, but those characters aren't present in the actual string as we will see later.)

- The third screenshot is calling the `main` method and we see that `4123` is being passed through as `args[0]` which is then set as the port number which we can see reflected in the URL's of the first two screenshots.

- As a result of the method calls from the first two screenshots, the else if statement in `handleRequest` is ran since `/add-message` is present in the URL. As a result of this, a String array called `parameters` is created which contains two Strings that are split from the Query of the URL at the `=`. The first string would be everything after the `?` until the `=` and the second string is everything after the `=`.

- After this, the if statement checking if `parameters[0].equals("s")` is ran and that is true in both cases as we can see from the URL and the description given above. Our method then updates `result` by adding `parameters[1]` to the end of the list. In the case of the first screenshot, this would add `"Hello"`, in the second screenshot, this would add `"How are you"`. Both of these method calls are updating the value of result by adding an additional element.

![Image](completeServer.png)

- This screenshot is showing the server printing out all of the strings we've added. An important thing to notice here is that the URL is just `localhost:4123` meaning that the path is just `/`. As a result, when the `handleRequest` method is called and the URL is passed through, the first if statement is called. 

- This if statement edits the value of `str` from just being an empty string to containing all of the strings we've previously added and stored in `result` and separating each of them with a `\n` character (This character prints each string on a new line which can be seen in the screenshot). After looping through all the values in `result` and adding them to `str`, `str` is returned and displayed on the website. 

- An important thing to note is that this URL never causes result to be edited because the else if statement is never called since the path is just `/`.

## Part 2 - Buggy Programs

- If we take the `ArrayExamples.java` file from Lab 3 and look at the `reversed` method, we will find a very glaring issue as soon as we test it. We will discuss what the specific issue is and how to fix it later, but first let's look at a test that returns a result we aren't expecting.

- If we create a JUnit Test such as this one: 
```
@Test
public void testReversed(){
  int[] input1 = {1,2};
  assertArrayEquals(new int[]{2,1}, ArrayExamples.reversed(input1));
  }
  ```
-



