# WEEK 1 Blog 
## Step by step tutorial on working with remote access!

**Step 1: Installing VS Code** <br><br>
Go to [Link](https://code.visualstudio.com) and download the latest stable build. Run installation and then open up the IDE. It should look something like the picture below. <br><br>
![Image](https://i.imgur.com/DUMjBVl.png) <br>
*Go to new file if you need to start a new assignment, open if you need to finish up something you already started and clone git repository if you need to work on a folder that is uploaded in github.* <br><br>
**Step 2: Remotely Connecting** <br><br>
- Go to [Link](https://sdacs.ucsd.edu/~icc/index.php) and change global password (but keep AD login the same). 
- Find the course specific account which is `cs15lsp22awm`. 
- As I am using a mac which already has ssh installed, open up new terminal in VS Code(in the folder that I want to connect remotely) and type in `ssh cs15lsp22awm@ieng6.ucsd.edu` which leads to the image below.<br>
- First Time <br><br>
![Image](https://i.imgur.com/gKcvni4.png)<br>
*If it is the first time, just say yes when they ask whether you are sure you want to be connecting*<br>
- Second Time <br><br>
![Image](https://i.imgur.com/XUj3Jp6.png)<br><br>
**Step 3: Trying some commands**<br><br>
First lets go over some simple terminal commands and what they do.<br>
`cd`: changes the directory that you are working in.<br>
`pwd`: shows you the current path you are working in. <br>
`cp`: 
`ls`: once you are in a directory (using cd) ls gives you a list of contents in that directory. <br>
`ls -lat`: gives details about the contents (l) (including hidden files (a)) like author, permissions, modified date, etc. and organizes the content by time/date (t). <br> 
- Local client <br><br>
![Image](https://i.imgur.com/Dk9uAoD.png)<br>
![Image](https://i.imgur.com/qEqdQEZ.png)<br>
- Remote server <br><br>
![Image](https://i.imgur.com/Ap31YWY.png)<br><br>
**Step 4: Moving files with scp**<br><br>
You can use scp to move files between local client and the remote computer.<br>
- Create a .java file in VS Code (Something like the class below).<br><br>
![Image](https://i.imgur.com/GdhX0RI.png)<br>
- Run it using `javac WhereAmI.java` (press enter) and then run `java WhereAmI`. With javac and java you can run specific classes in a .java file. After that use `scp WhereAmI.java cs15lsp22awm@ieng6.ucsd.edu:~/`. *Make sure to run it from the directory where WhereAmI.java is saved*.<br><br>
![Image](https://i.imgur.com/sEjJICy.png)<br>
- When you log into your remote account, using ls you should be able to see the file stored.<br><br> 
![Image](https://i.imgur.com/2wC2nN9.png)<br><br>
**Step 5: Setting an SSH key**<br><br>
- On local client. 
1. `ssh-keygen`
2. This generates a public and private rsa key
3. Make sure you save the key in Users/meghachouthai/.ssh/id_rsa. 
4. follow the terminal commands but press enter when asked for a passphrase (do not create a passphrase)
5. `ssh cs15lsp22awm@ieng6.ucsd.edu`
- On remote server
1. `mkdir .ssh`
2. exit
- on local client
1. `scp /Users/meghachouthai/.ssh/id_rsa.pub cs15lsp22awm@ieng6.ucsd.edu:~/.ssh/authorized_keys` which moves the key from local client to remote server. 
2. now you do not need to enter password each time.<br><br>
![Image](https://i.imgur.com/DU2xKht.png)<br><br>
**Step 6: Optimizing Remote Running**<br><br>
Some pointers on how to optimize remote running.<br>
- running `ssh cs15lsp22awm@ieng6.ucsd.edu + "<given command>"` in terminal runs the given command in the remote server directly, so you do not have to run an additional step to connect to the server as seen below.<br><br> 
![Image](https://i.imgur.com/2wC2nN9.png)<br><br>
- Use semicolons to run more than one command. *the commands are interspaced by the semi-colon.*
