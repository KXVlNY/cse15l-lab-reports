# Lab Report 3: Streamlining `ssh` Configuration

## Setting Up a `./ssh config` File by Using the Git Bash
**This instruction is for **Windows machines ONLY**
Generally, in Windows machine, the SSH config file stored in the following location: 
`/C/Users/PC_USER_NAME/.ssh/`
![Directory](directory.jpeg)

Go to the `.ssh` directory `/C/Users/PC_USER_NAME/.ssh/`, 
click right mouse button and choose **"Git Bash Here"**
![GitBash](GitBash.jpeg)

Create a file named "config" with the following command:
`touch config`
Now open the config file with the command:
`nano config`
![touch](touch.jpeg)

Now write the following lines inside the config file:
![nano](nano.jpeg)

Save the config file with the command: `ctrl + o`
Then, hit `enter`
![configsave](configsave.jpeg)

Now try opening `~/.ssh/config` on your computer
(I opened it with a VSCode)
![sshconfig](sshconfig.jpeg)


### Logging into `ieng6` Account by Using `ssh ieng6`
Now we can use `ssh ieng6` that’s faster and easier to type!
![sshieng6](sshieng6.jpeg)


#### Copying a File by Using `scp` Command
![Pic1]()
