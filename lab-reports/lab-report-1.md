# Lab Report 1
Sarah Burbach

Please note that this tutorial and the screenshots are assuming that you have a mac computer. If your computer is windows, there may be a few extra/different steps you need to take!

## Installing VScode
First, you need to install VScode! Go to [this website](https://code.visualstudio.com/) and install the correct version for your specific computer and operating system. 

Once it has been sucessfully installed, it should look something like this: 

![VScode-Image](/lab-report-images/vscode-open.png)

However, you should know that yours won't have the 'Recent' section that is shown in this image. My VScode has this section becuase I've opened folders and files previously using VScode and this is not the first time I've opened the application!

## Remotely Connecting
The next step is to remotely connect to a UCSD computer.

First, you need to find your course specific username. My username for this course is 'cs15fa22ac', but you can check your username at [this link](https://sdacs.ucsd.edu/~icc/index.php).

Now, you should open a new terminal (File -> Terminal -> New Terminal), then type the command:
`ssh cs15fa22ac@ieng6.ucsd.edu`

The first time you connect to this server, you will be prompted to verify the authenticity of the host. You should type 'yes' in response to this prompt. This does not appear in the screenshot provided below, becuase the login showed is not my first login. 

Then you will be prompted to enter your password. Note that when you are typing your password, nothing will appear in the terminal (ie. it will look like you aren't typing anything) -- this is normal! If you are having trouble with your password, you can reset your password by following the instructions in [this doc](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit).

This is what a sucessful login looks like:

![Successful-Connect-Image](/lab-report-images/successful-connection.png)

## Trying Commands
Now that you are connected, you can test out some commands on the remote computer! 

One example of a command you can try is `ls`, which will list all of the files and folders in your current working directory. For example, here is the result I recieved when typing the command for the first time on the remote server:

![ls-image](/lab-report-images/ls-command.png)

Another command you can try is the `cat` command, followed by the path to a file. This will print the contents of that file in the terminal. Here is an example of me running this command on the remote computer:

![cat-image](/lab-report-images/cat-image.png)

## Moving Files with scp
Now that you've tried out a few commands, you can also also try moving files to a remote computer with the command `scp`.

First, you want to make a file (in this case, the file was called WhereAmI.java) and save it locally on your computer. Compile and run in on your computer. This is what this should look like:

![whereami-image](/lab-report-images/whereami-image.png)

Then type the command `scp WhereAmI.java cs15lfa22ac@ieng6.ucsd.edu:~/`, remembering to replace my course username with your own. This is what a sucessful transfer looks like:

![whereami-transfer](/lab-report-images/whereami-transfer.png)

Now you can log into your ssh account (as described previous) and use the compand `ls` to confirm that the file has been transfered. Then you can compile and run the file on the remote computer. This will look something like this:
![whereami-remote](/lab-reports/lab-report-images/whereami-remote.png)

## SSH Keys
Now, you can create a key to allow you to login to your ssh account without entering the password every time. 

First, you need to create a key on local computer. First, run the command `ssh-keygen` on your local computer. You will need to set the folder for the key to save. Then, when prompted for the passphrase, leave it blank and just press enter. This will generate a result like this:

![local-key](/lab-report-images/local-key.png)

Next, log into the remote computer and enter the command `mkdir .ssh`. The `mkdir` command will create a new directory called '.ssh', where we will transfer the key file to in the next step.

![remote-mkdir](/lab-report-images/remote-mkdir.png)

Finally, you can transfer the public key (named id_rsa.pub) to the remote computer using the `scp` command, as shown below:

![key-transfer](/lab-report-images/key-transfer.png)

After completing all of these steps, you should be able to login without password: 

![login-nopassword](/lab-report-images/login-nopass.png)

## Optimizing Remote Running
Now that we've learned all these skills, we can attempt to optimize the process of copying a file to a remote server and running it. The goal here is to get the total number of keystrokes for this entire process to under 10, but I was unable to do this. This is the best attempt I was able to get:

![optimization-attempt](/lab-report-images/optimization.png)

In this case, I am struggling to understand how it is possible to get such a low number of keystrokes for a few reasons:
* First, we need to login to the ssh to run commands on the remote server, and the username to do this 'cs15lfa22ac@ieng.ucsd.edu' is already more than 10 keystrokes. There is no shortcut that I know of to avoid typing this. I think that maybe we could use the up arrow to access the previous command (and have the previous command be just the username), but I don't understand how this saves much time overall becuase you still have to type the username.
* Second, I am not sure how to copy a file to a remote server without the use of the scp command. I was thinking maybe we could use the cp command once already logged into the remote server, but couldn't figure out how (if you even can) to access the local computers directory from the remote server. 
