# Lab Report 1
Due 9/30/22

## Installing VScode
First, you need to install VScode! Go to [this website](https://code.visualstudio.com/) and install the correct version for your specific computer and operating system. 

Once it has been sucessfully installed, it should look something like this: 
![VScode-Image](/lab-reports/lab-report-images/vscode-open.png)
However, yours won't have the 'Recent' section that is shown in this image. My VScode has this section becuase I've opened folders and files previously using VScode.

## Remotely Connecting
The next step is to remotely connect to a UCSD computer.

First, you need to find your course specific username. My username for this course is 'cs15fa22ac', but you can check your username at [this link](https://sdacs.ucsd.edu/~icc/index.php).

Now, you should open a new terminal (File -> Terminal -> New Terminal), then type the command:
`ssh cs15fa22ac@ieng6.ucsd.edu`

The first time you connect to this server, you will be prompted to verify the authenticity of the host. You should type 'yes' in response to this prompt.

Then you will be prompted to enter your password. Note that when you are typing your password, nothing will appear in the terminal (ie. it will look like you aren't typing anything) -- this is normal! If you are having trouble with your password, you can reset your password by following the instructions in [this doc](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit).

This is what a sucessful login looks like:
![Successful-Connect-Image](/lab-reports/lab-report-images/successful-connection.png)

## Trying Commands
Now that you are connected, you can test out some commands on the remote computer! 

One example of a command you can try is 'ls', which will list all of the files and folders in your current working directory. For example, here is the result I recieved when typing the command for the first time:
![ls-image](/lab-reports/lab-report-images/ls-command.png)

## Moving Files with scp


## SSH Keys

## Optimizing Remote Running