# **CSE 15L Lab Report 4**

## **Part 1 - Editing GitHub Files from the Command Line**

- The first step of this excersize from the lab is to log into our ieng6 account. To do this, we need to type `ssh cs15lsp23ad@ieng6.ucsd.edu` into the terminal (Note: "ad" can be replaced with your specific course username) and then hit `<enter>`.

- Assuming you have completed the lab setup before this exercise, this command should log you into your ieng6 account directly without any prompt for your password.

![Image](loggedIn.png)

- After successfully logging into ieng6, we want to clone the lab7 github repository. To do this, we need to go to the fork we created prior to starting this exercise and we need to click the green code button near the top right, and copy the link present under the "SSH" section as seen in the image below.

- Note: If you simply copy the URL to the repository or the link under the "HTTPS" section, later steps will not work properly because the SSH key created during the setup for this exercise will not allow you to automatically push to the repository.

![Image](copyRepo.png)

- After copying the SSH link that's shown above, go back to your terminal and type in the command `git clone git@github.com:anc034/lab7.git` (Note: that last part should be your respective link) and then hit `<enter>`.

- If you followed the steps correctly, this command should copy the GitHub repository into your current directory on the ieng6 machine as seen below.

![Image](gitClone.png)

