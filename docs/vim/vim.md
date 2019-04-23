# Vim

## Autoformat xml
```bash
:'<,'>!xmllint --format -
```

## Get back selection after indentation
```bash
gv
```
Get this feature forever
```bash
vnoremap < <gv
vnoremap > >gv
```

## Run command in shell
```bash
:!<command>
:!    # Run the last external command
:!!   # Repeats last command
:silent !<command> # Eliminates the need to hit enter after the command is done
:r !<command>      # Puts the output of <command> into the current buffer
```

## Replace words with yanked text
### First way
```bash
yiw
# Move to new word
viwp
viw"0p  # Redo
```

### Second way
```bash
yiw
# Move to new word
ciw[CTRL-R]0[Esc]
. 	# Redo
```

## Delete all lines containing word
```bash
:g/<word>/d
```
