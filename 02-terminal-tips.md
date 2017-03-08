# Terminal Tips
## Opening files and directories
When poking around directories and file in the terminal it is nice to be able to open a file or directory directly from the terminal.

For Files: 
```
open -a '<program name>` example.txt
```

`<program name>` would be the name of the program you would like to use to open up the file.

For Directories:
```
open -a '<program name>` example/
```

## Show all files and directories
When digging around in the terminal is great to be able to list all files, hidden files, and directories. Also it is great to be able to view the permissions, owner, file size, and last modified. For this we would run:

```
ls -lah
```
A breakdown of this command is:

`ls` is to list directory contents.
`-l` is to give the long listing. 
`-a` is to show hidden files and directories
`-h` is to print the file file size in a human readible format.

For this command I personally like to alias this to `ll`. For this it would be `alias ll='ls -lah'`

## Running previous command
From time to time we may need to run the previous command but with something in front of it. Example being running `vim example.txt` but finding out it is read only and requires `sudo`.

To add `sudo` before `vim example.txt` without having to retype `vim example.txt` we would use:

```
sudo !!
```

The `!!` is grabbing the previous command and placing it where the `!!` is.

## Cycling through previous commands
While in our terminal we may need to rerun a command that was run 5 commands ago. Rather than retyping that command we can hit the `up arrow` 5 times to get back to that command. An example of this ussage:

I ran these commands in order in my terminal

```
print 'hello'
cd example/
ls -lah
```

Now I want to rerun the command `print 'hello'`. to do this I would hit the `up arrow` 3 times and it would grab that command again.

## Searching for previously ran commands
One trick we can do to run a previous command that may be high up than we want to click the up arrow for is to hit `ctrl+r`. Once we do this we can start typing and it will try and autocomplete and find the command you are searching for. Once you find it you can just hit `enter` and the command will run.

## Exiting current terminal action
While searching for a previous commands or while a script is running we may want to stop it immediately. To do this is we would press `ctrl+c`. This will attempt to terminate what ever the terminal is doing.