# New developer tips and tricks:
These are some of the tips and tricks I have picked up along the way and wish I knew when I first started out.


## Terminal / Bash Profile happy fun times
#### What is bash?

>(Bourne Again SHell shell) A command line processor for Unix from the Free Software Foundation. It is the de facto command processor in Linux and Mac. See Bourne shell and Free Software Foundation. 
source: [yourdictionary](http://www.yourdictionary.com/bash-shell)

#### What can the terminal + bash profiles do?
A LOT.

#### What should I know to start?
*(For this we are going to assume `.zshrc` file is used. For the most part the same can be applied to the `.bashrc` and `.bash_profile`).*

- Your `.zshrc` file lives in your `HOME (~/)` directory.
- After making edits to the `.zshrc` files you will need to run `source ~/.zshrc` in the terminal window. Also if you open a new terminal window you will automaticlly get the fresh changes.

#### Editing my .zshrc file is a pain
If you have to open a text editor and find your `.zshrc` file every time you want to make edits I would agree.

Luckily in bash we can create aliases for arbitrary commands. So for creating an alias to edit my `.zshrc` file I would create three aliases like this:

```
alias __open_vsc="open -a 'Visual Studio Code'"
alias __edit_zsh="__open_vsc ~/.zshrc"
alias __source_zsh="source ~/.zshrc"
```

- `__open_vsc` will open files / directories in `Visual Studio Code` ( This can be changed to Sublime, Atom, Dreamweaver (Please don't use Dreamweaver) ). 
- `__edit_zsh` will open your `.zshrc` file in `Visual Studio Code`
- `__source_zsh` will source your `.zshrc` file in the currently open & active terminal window

Then to use these commands in your terminal you would simply type the alias name (ex: `__edit_zsh`) and hit `enter`.

#### My project require me to run a bajillion commands, help?
Rather than chaining a bunch of aliases together we can create `bash functions`. Much like functions in other programming languages they let us run a chunk of commands and pass in values.

A basic example to start up a rig project:

```
# Start the outrigger and project box.
startup() {
  rig start;
  eval "$(rig config)";
  docker-compose up -d;
}
```

And to use this we would simply type `startup` and hit enter. Note, the `()` at the end of `startup` is not needed.

For a more complex function we could do something like this:

```
# Get enviroment URL
#$1 country code
#$1 enviroment code
open-site() {
  if [ $2 == 'local' ]; then
    open http://$1.cool-project.vm/
  else
    open http://$1.$2.cool-project.com/
  fi
}
```

Which to use this would be something like `open-site us local` and it would produce a url like: `http://us.cool-project.com`. If we did `open-site us dev` it would give us a URL like `http://us.dev.cool-project.com`.

***Note:** If your variable contains spaces wrap it in double quotes.*

#### I wish I could see all of the files, directories, and hidden goodies
You can by running `ls -lah` or if you are on [zsh](https://ohmyz.sh/) or alias it, the commad is simply `ll`.

#### I was trying to do this thing with a long command but now I need sudo.
Cake, run `sudo !!` and you will be prompted to run your last command with sudo in front. In fact you can put anything in front of the `!!` (Bang Bang), it just simply tells the terminal you want the previous run command.

#### So I ran a thing like 3 commands ago.
Super cake, hit the up arrow 3 times to get back to that commands.

The up arrow will start to cycle through previously run commands.

#### So I ran this command like 5 minutes ago and I need to run it again.
Less cake, still easy.
- Hold `CTRL+r`, this will bring up a prompt 
- Start typing the command and when what you want appears hit enter

#### So I ran the wrong script and it is chugging away.
Hold `CTRL + c` and 9 times out of 10 ever time it will eject you out.

#### Someone told me to try vim, how do I exit?
- Hit `ESC`
- Type `:q!` to quit, `:wq` to save changes and quit



## Table of Contents
- 01-Bash Profile
  - Bash scripting
- 02-Terminal-Tips
  - Opening file / directory with application
  - Showing all files and directories 
  - Running previous command
  - Cycling through previous commands
  - Searching for previous commands 
  - Exiting current terminal action
- 03-Apps
  - Text Editors 
    - Atom
    - Sublime Text 3
    - Visual Studio Code
    - MacDown
  - IDE
    - PHPStorm
  - Utility
    - Alfred 3
    - Iterm2
    - Last Pass
    - Sequel Pro (SQL Pancakes)
- 04-Tools
  - Homebrew
  - Oh-My ZSH
  - NVM
  - RVM
  - Tmux
- 05-Utility-Sites
  - Regex
    - Regexr
    - Regex101
  - Timers
    - Toggl
  - Drupal
    - Multiple versions of drush
    - Drush Commands
- 06-Notes
  - Google Keep
  - Evernote
  - Microsoft One Note
- 07-Gotchas
  - OSX Sierra
