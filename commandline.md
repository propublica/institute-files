# The Command Line

Command line, terminal, shell, CLI ("command line interpreter" or "command line interface").

## Why do we use the command line?

* It helps make some things faster
* There are tools that only exist for the CLI and don't have a point-and-click interface.
* It opens the door to programming languages like Ruby


## Using the command line

### Opening a terminal

**Mac**: Open the `Terminal` app. (It's inside Applications->Utilities, but you can also get to it by searching.)

**Windows**: Press the Windows key and search for `PowerShell`. You can also press Windows-R to get the "run" menu and type in `cmd`, then press enter.


### You Are Here: Moving around

When you use the Finder or File Explorer, your window is always open to a specific folder. You can go to other folders by clicking on them. Similarly, a terminal is always _in_ a specific folder. Instead of clicking, you use text commands to figure out where you are and to move around.

By default, the terminal starts in your home directory.

| Mac  | Windows | Description |
| ---  | ------- | ----------- |
| `pwd`| `pwd` | shows you what directory you're in (and the full _path_ to that place) |
| `ls` | `ls`   | shows you a list of all things in current directory |
| `cd Desktop` | `cd Desktop` | moves to the `Desktop` directory inside the current directory |
| `cd /` | `cd C:\` | moves to the "top" of your hard drive |
| `cd /Users` | `cd C:\Users` | moves to the folder called `Users` (if there is one) in your hard drive |
| `cd ~` | `cd %HOME%` | moves back to your home directory |

The thing after the `cd` is an "argument" -- it's something you give to the `cd` command to do whatever it is the command does. `cd` moves the terminal "into" another folder, like double-clicking in Finder or File Explorer.

(On Windows, doing `cd` without an argument simply shows you the current directory, like Mac `pwd`. On Mac, doing `cd` without an argument moves to your home directory.)

* _Relative paths_: you can get into `Desktop` from your home directory by doing `cd Desktop`, because `Desktop` is inside your home directory. Similar to the way the `<link href="...">` tag works when something is in the same directory.
* _Absolute paths_: you can get into `Desktop` directly from _anywhere_ by entering in the _absolute path_ or _full path_ of the Desktop folder `cd /Users/mtigas/Desktop` (Mac) or `cd C:\Users\mtigas\Desktop` (Windows). See the `pwd` / `echo %cd%` command to see the current absolute path.

**Common path & file aliases**

| alias | description |
| ----- | ----------- |
| `~` (Mac) or `$HOME` (Windows) | your home directory |
| `.` | the current directory |
| `..` | the directory above this one |
| `*` | all files and directories inside this directory |
| `*.html` | all files with names that end with `.html` inside this directory |

**Tip:** If you mistype and want to cancel the current line you're in the middle of, press `Control-C`.

_**Example**: From a newly-opened terminal, try the following._

* `ls`
* `cd Documents`
* `pwd`
* `ls`


_**Exercise**:_

* Move into the `GitHub` directory on your computer that was created by the GitHub Desktop app yesterday.
  - On Mac it's in your home directory; on Windows, it's inside `Documents` in your home directory.
* Move into one of the repo directories, like `awesome-project` or `hello-propubdata` and get a list of what's inside that directory.
* Use Finder or File Explorer to look at that directory. Are there any differences between what's listed in the user interface vs in the command line?

### Doing things to files

| Mac  | Windows PowerShell | Description |
| ---  | ------- | ----------- |
| `mv index.html something.html` | `mv index.html something.html`  | renames `index.html` to `something.html` |
| `cp index.html index-backup.html` | `cp index.html index-backup.html` | makes a copy of `index.html` to a new file called `index-backup.html` |
| `rm something.txt` | `rm something.txt` | deletes the file called `something.txt` in the current directory |
| `mkdir MyFolder` | `mkdir MyFolder` | creates a directory named `MyFolder` inside the current directory |
| `cp -r MyFolder MyFolderCopy` | `cp MyFolder MyFolderCopy` | makes a copy of the directory `MyFolder` to a new file called `MyFolderCopy` |
| `rm -fr MyFolder` | `rm MyFolder` | deletes the directory named `MyFolder` |

### Cool things you can do

| Mac  | Windows | Description |
| ---  | ------- | ----------- |
| `find .` | `dir -r` | shows you all the files and folders in the current directory, and all the files and folders inside all _those_ folders and so on |
| `open .` | `explorer .` | opens a Finder or File Explorer to the current directory |
| `open some_file.txt` | `explorer some_file.txt` | this does the same as double-clicking on `some_file.txt` if you were in a Finder or File Explorer |
| `subl some_file.txt`‡ | `subl some_file.txt`‡‡ | opens up `some_file.txt` in Sublime Text |
| `subl .`‡ | `subl .`‡‡ | opens up Sublime Text with this folder in the sidebar |

* ‡ You need to run this command first:
  ```
  sudo ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
  ```
* ‡‡ Not installed in Windows by default; involves [editing some settings](https://scotch.io/tutorials/open-sublime-text-from-the-command-line-using-subl-exe-windows#adding-sublime-to-your-path) to turn it on.

| Mac  | Windows | Description |
| ---  | ------- | ----------- |
| `grep "<p>" index.html` | `select-string "<p>" index.html` | shows you all lines that contain `<p>` inside the `index.html` file in the current directory |
| `grep "text" *` | `select-string "text" *` | look for _text_ in all files in the current directory |
| `grep -r "text" .` | --- | look for _text_ in all files inside the current directory and all directories underneath |

## Getting help

Most commands can give you information on how to use them. Usually you get it by doing `-h` or `--help` or `/?` or `/help`.

The following lists some information on how to use the `git` command-line command:

```
git --help
```

You _should_ get something like:

```
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

...
```


## Tips & Tricks


### Stuck?

If a command seems stuck, you can press "Control-C" on your keyboard to cancel it.

If you only pass the first argument to `grep` or `find`, for example, it waits for some input instead of searching files in your directory...

```
# mac
grep "text"

# windows
find "text"
```

...a you'll need to press Control-C to quit the command.

### Autocomplete

The modern command line has an autocomplete feature which can help you quickly enter in commands, file names, and directory names.

Try it! From a fresh terminal, type `cd Desk` and press the tab key; the remaining letters in `Desktop` should automatically appear.

### Jump to the beginning or end of the line.

If your keyboard has "home" and "end" keys, those will go to the start or end of the line, like in Word or other text editors.

Otherwise:
* `Control-A` will jump the cursor to the start of the line.
* `Control-E` will jump the cursor to the end of the line.

Helpful if you've mistyped the beginning of a command.

### The "say" command (Mac only)

The `say` command is fun: `say hello`

### Administrator privileges

Sometimes you need to install software from within a command-line. If it doesn't work normally, you will have to run the command with administrator privileges.

On Windows, you need to open a terminal in Administrator Mode.

* Click the Start menu and start typing in "Command Prompt".
* When the "Command Prompt" app appears, right-click and choose "Run as Administrator".

On Mac, you can prepend `sudo` to the command you originally tried.


# More Resources

* [The Command Line Crash Course](http://cli.learncodethehardway.org/book/)


# Git on the Command Line

* [The Command-Line Git Cheat Sheet](https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf)
