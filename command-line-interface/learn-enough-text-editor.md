<a href="http://www.learnenough.com/text-editor-tutorial"><img style="height:250px" src="https://softcover.s3.amazonaws.com/636/learn_enough_text_editor/images/cover-web.png" /></a>

# VIM
## Starting Vim in Terminal
`vim` - starts Vim in Terminal
`:q` - quit a file (must be saved)
`:q!` - force quit a file, discarding any changes

## Navigating
`Arrow keys` - move around
`0` - go to beggining of line
`$` - go to end of line
`G` - move to the end of file
`1G` - move to the beginning of file
**Ctrl-F** - move forward one screen
**Ctrl-B** - move backward one screen
`/<string>` - search
`n` - move to next searh result
`N` - move to previous search result

## Editing
`vim <filename>` - open/create file in Vim
`i` - enter / exit insertion mode
`ESC` - exit insertion mode, enter normal mode
`x` - delete the symbol in normal mode
`dd` - delete the line in normal mode
`p` - put (paste) deleted text
`u` - undo

## Saving files
`:w` - save (write) a file
`:wq` - write and quit a file