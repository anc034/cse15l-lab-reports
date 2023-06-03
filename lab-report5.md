# **CSE 15L Lab Report 5**

## **Debugging Scenario**

### **Step 1: Viewing the EdStem Post**

- For this lab report we will be running through a debugging scenario similar to those from [Lab 9](https://ucsd-cse15l-s23.github.io/week/week9/).

- To begin we need to look at the EdStem post made by the student who is having issues with their code in order to start figuring out what the possible issue is and how we can help.

![Image](edstemDebug.png)

- Based on this post, we have a starting point for debugging the code since we know the error being thrown is a `NumberFormatException` and we're told that the code only throws an error when the if statement is called so we can assume the bug is somewhere in that section of the code.

- Based on this knowledge from the post, we can move to the next step.

### **Step 2: Suggesting Commands for Debugging**

- In this step, we are acting as the TA for this student and will give advice so they can definitively identify the bug based on the EdStem post shown above.

- Based on the post, we can see that the error occurs at line 3 in the Multiply.java file. As a result, my suggestion to the student would be to create a print statement using `System.out.println` and place it on the line directly before the code that's currently on line 3. I would advise them to print the variable that is being parsed so that we can identify if it is correct or if it is the source of the bug. (Note: We know the error comes from `Integer.parseInt` on line 3 by looking at the Ed




