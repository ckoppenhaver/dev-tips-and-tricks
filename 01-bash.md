#Bash Profile Goodness
The bash profile is the file where your Unix system looks for all of your PATHs, alias', enviroment variables, and other goodies. 

## Bash Scripting
### Alias
A bash alias is a short string that can be assigned different a single or multiple commands. This can be useful if you have a long command that you need to run multiple times.

Creating an alias:

```
alias='cd ~/'
```

It's good to note that there cannot be a space around the "=" and the end of the line should **not** have a semicolon.

### If Else and Check for null / empty
In the bash profile the need for creating if / else statements or checking for if a variable is empty may be needed. It is good to note that items inside of the statements will be ran just as if they were typed into the command line.

#### If Statement
```
if [ 'thing' == 'thing' ]; then
  print "woohoo";
fi
```

#### If Else Statement
```
if [ 'thing' == 'thing' ]; then
  print "woohoo";
else
  print "womp womp";
fi
```

#### Checking for null / empty
```
if [ -z 'thing' ]; then
  print 'So empty!';
fi
```

## Bash Functions
In your bash profile you may need to find the need for functions. Functions are handy when you find yourself using the same set of scripts but need to pass it variables. 

```
# $1 = Your name
hello-world() {
  print "Hello World! My name is $1";
}
```
To call and use this function you would write in your command line `hello-world Bob`. Bob being the variable `$1` which is our name.

## Bash Variables
Sometimes we may need to create and use a bash variable but not really set a enviroment variable. This can be done by doing the following.
```
URL="google.com";
print "A useful URL is $URL";
``` 
It is good to note here that the variable `URL` is capital and there are no spaces around the `=`. Also when we go to use the `URL` variable we call it with a `$` in front like this: `$URL`.