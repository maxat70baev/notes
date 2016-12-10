<a href="http://www.learnenough.com/command-line-tutorial"><img style="height:250px" src="https://softcover.s3.amazonaws.com/636/learn_enough_command_line/images/cover-web.png" /></a>

## Getting out of trouble
**Ctrl-C** - cancel
**ESC**

## Manual and Less pages
`man <command>` - display manual page for command
`less <file>` - view file contents interactively
**Ctrl-F** - move forward one page
**Ctrl-B** - move back one page
`G` - move to end of file
`1G` - move to beginning of file
`/<string>` - search file for *string*
`n` - move to next searh result
`N` - move to previous search result
`q` - quit man/less

## Editing the line
**Ctrl-A** - move to beginning of line
**Ctrl-E** - move to end of line
**Ctrl-U** - delete to beginning of line
**Ctrl-W** - delete last word
**Option-click** - move cursor to location clicked
**Option-Right/Left arrow key** - move one word forward/back
`\` - line continuation

## Cleaning up
`clear` - clear the screen (**Ctrl-L**)
`exit` - exit window/tab (**Ctrl-D**)

## Redirecting and appending
`>` - redirect output to filename, e.g. echo foo > foo.txt
`>>` - append output to filename, e.g. echo bar >> foo.txt
`echo >> <filename>` - appends a newline to *file*
`cat <file>` - print contents of *file* to screen
`diff <f1> <f2>` - diff *files* to screen

## Listing
`ls` - list directory or file
`ls -l` - list long form
`ls -rtl` - long by reverse modification time
`ls -a` - list all (including hidden)
`ls -h` - list human readable

## Renaming, copying, deleting
`touch <file>` - create an empty *file*
`mv <old> <new>` - rename (move) from *old* to *new*
`cp <old> <new>` - copy *old* to *new*
`rm <file>` - remove (delete) *file*
`rm -rf` - force-remove file

## Downloading files
`curl <url>` - interact with *urls*

## Repeating previous commands
**Up arrow key** - retrieve previous commands
**Ctrl-R** - search interactively through previous commands
`!!` - repeat previous commands
`!<characters>` - "repeat last command that started with those characters"

## Heads and tails
`head <file>` - display first part of file
`tail <file>` - display last part of file

## Wordcount and pipe
`wc <file>` - count lines, words, bytes
`<command1> | <command2>` - pipe command 1 to command 2, i.e. command 2 takes as an input an output from command 1

## Grepping
`grep <string> <file>` - find string in file
`grep -i <string> <file>` - find case-insensitively
`open -t "$(grep -il <string> *)"` - opens file in current directory that contatins *string*
`open -t "$(grep -il <string> .)"` - opens file in current directory and its subdirectories that contatins *string*

## Processes
`ps` - show processes
`top` - show processes (sorted)
`kill -15 <pid>` - kill a process
`pkill -15 -f <name>` - kill matching process

## Directories
`~` - home directory, i.e. /Users/username/
`..` - one directory up
`.` - current directory
`mkdir <name>` - make directory with name
`mkdir -p <dir>/<subdir>` - make *intermediate directories* as necessary
`pwd` - pring working directory (display full path)
`cd ~` - change to home directory
`cd <dir>` - change to directory
`cd ~/<dir>` - cd relative to home
`cd ..` - cd one directory up
`cd -` - cd to previous directory
`find <dir> -name <file/folder name>` - find files and directories
`cp -r <old> <new>` - copy recursively
`rmdir <dir>` - remove (empty) *dir*
`rm -rf <dir>` - remove *dir* and contents (recursive and forced)
`grep -ri <string> <dir>` - grep recursively (case-insensitive)

## Combining commands
`<command1> ; <command2> ; ...` - *commands* run in sequence
`<command1> && <command2> && ...` - *commands* run consecutively only if previous *command* succeeded
`<command1> || <command2> || ...` - execution of *command1* OR *command2*, stopping on the first succesful *command*

## Miscellaneous
`#` - comment out
`source <profile>` - sourcing updated *profile*
`alias <newcommand>='<command>'` - attaching alias to a *command*
`echo $PATH` - show the current path
`export PATH="/<dir>:$PATH"` - add *dir* to the current path
`chmod +x <filename>` - make *filename* executable, i.e. add "execute bit" (x)
`unzip <filename>.zip` - unzip a ZIP archive
`chflags hidden <filename>` - hide *filename* in GUI (Finder)
`chflags nohidden <filename>` - unhide *filename* in GUI (Finder)
`chmod -R +rw <directory>` - change permissions recursively

