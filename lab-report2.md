# **CSE 15L Lab Report 2**

## Part 1 - String Server
![Image](StringServer.png)

- This screenshot is showing the code for the String Server that we created and are hosing locally. The `handleRequest` method in the `SearchEngine` class deals with checking the URL that the user is inputting in their search engine. 

- The `main` method in the `StringServer` class is what allows us to use the command line to input the port number to start the server in VS Code. In the following screenshots we will see how these two methods allow the user to add strings and see the total list of strings.

![Image](addHello.png) ![Image](addHow.png) ![Image](StringTerminal.png)

- The first two screenshots are showing two separate instances of adding a string to the server and the third screenshot shows the terminal commands necessary to start the server.

- The first two screenshots are each calling the `handleRequest` method and are passing through their specific URL's as the parameter. For the first screenshot it would be `localhost:4123/add-message?s=Hello` and for the second screenshot it would be `localhost:4123/add-message?s=How%20are%20you` (An important note is that the URL seems to add "%20" when there is a space in the string, but those characters aren't present in the actual string as we will see later.

- The third screenshot is calling the `main` method and we see that `4123` is being passed through as `args[0]` which is then set as the port number which we can see reflected in the URL's of the first two screenshots.


