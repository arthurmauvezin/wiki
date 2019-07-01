# Scripting examples

## Semicolon Usage
> : is equivalent to true command. 
When used with another bash substitution command for example, the command return true instead of the string.
Example:
```bash
${TEST1:=default1}
```
Assign default1 to TEST1 variable and return default1 (so, if the return string is a command, it will be interpreted by shell)

```bash
: ${TEST1:=default1}
```
Assign default1 to TEST1 variable and return true 

## Rename multiple files recursively
```bash
find . -iname <file_name_regex> -exec rename <old_name> <new_name> '{}' \;
```
> A cool tool to use in one folder is *rename* tool

## Rename multiple files in same folder
```bash
rename 's/<from>/<to>/' *.html
```

## Replace in file and diff
```bash
sed -e 's/<from>/<to>/g' <file_name> | diff <file_name> -
```

## Strict execution
```bash
set -euo pipefail
```

* set -e : If command fails, make the script exit (not resuming on next line)
* set -u : Treat unset variables as an error and exit
* set -o pipefail : cause a pipeline (command | command) to fail if one of the subcommand fails
* set -x : print each command before executing it

## Parameter substitution
### Default Value ${:-}
```bash
var=${parameter:-defaultValue}
```

### Default Value if not set ${:=}
```bash
echo ${parameter:=defaultValue}
```

!!! important
    This method do not work to assign values, use ${:-} instead.

### Display message if $value is not passed ${:?}
```bash
var="${1:?Please provide var}"
```

### Display message and run command ${:?}
```bash
_message="Please provide var"
var="${1:? $_message $(command)}"
```

### Variable length ${#}
```bash
length=${#var}
```

### Remove pattern - Front ${#} ${##}
```bash
url="https://www.google.com/test/mypage.html"

pagepath=${url#https://} 	# Return "www.google.com/test/mypage.html"
pagename=${url#*/}		# Return "/www.google.com/test/mypage.html"
pagename=${url##*/}		# Return "mypage.html"
```

### Remove pattern - Back ${%} ${%%}
```bash
url="https://www.google.com/test/mypage.html"

pagepath=${url%.html} 		# Return "https://www.google.com/test/mypage"
pagename=${url%/*}		# Return "https://www.google.com/test"
pagename=${url%%/*}		# Return "https:/"
```

### Find and replace ${//}
```bash
var="${x/unix/linux}"		# Replace first match
var="${x//unix/linux}" 		# Replace all matches
```

### Substring starting character ${::}
```bash
${parameter:offset:length}

x="nixcraft.com"
echo ${x:3:5}"			# Print craft
```

## Work with arguments/positional parameters

### Interesting values
Value | Meaning
--- | ---
$0 | Name of script
$N/${N} | Nth argument passed to script (brackets are mandatory after $9)
$# | Number of arguments passed to script
$@ | All arguments passed to script

### Check if argument is an option
```bash
if [ "${1#-}" != "$1" ]; then
        ...
fi
```

### Check if argument is some value
```bash
if [ "$1" = 'some-value' ]; then
        ...
fi
```

### Add positional parameters before arguments
The following script adds newcommand before other positional parameters.
```bash
set -- newcommand "$@"
echo "$@"
```

## Check if string is part of string
```bash
string='My long string'
if [[ $string == *"My long"* ]]; then
  echo "It's there!"
fi
```

## For each argument
```bash
for var in "$@"
do
    echo "$var"
done
```

## Obfuscate password
```bash
echo ${PASSWORD//[[:ascii:]]/*}
```

## Print decorated messages
```bash
print_decorate_message () {
        message=$1
        message_length="${#message}"
        message_decorate_length=$((message_length + 2))
        decorate_line=$(printf "%-${message_decorate_length}s" "-")

        echo "+${decorate_line// /-}+"
        echo "| ${message} |"
        echo "+${decorate_line// /-}+"
}
```

## Get script file path and name
```bash
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
SCRIPT_NAME="$(basename "$0")"
```

## If string is empty
```bash
if [ -z "$my_string" ]
then
        echo "String is empty"
fi
```

## Insert line at specific line
```bash
line_number=3
new_line="my new line"
sed -i "${line_number}i${new_line}" my_file
```

## Insert line after a specific line
```bash
line_number=3
new_line="my new line"
sed -i "${line_number}a${new_line}" my_file
```

## Replace some text on line matching with word
```bash
sed -i '/<word>/s/<from>/<to>/' my_file
```

## Grep exclusion
```bash
grep -r --color --exclude-dir={custom,lib,scripts} --exclude={*.xml,error_log} "beta" .
```

## Extract string match between words from file
### Grep way
```bash
grep -oP '(?<=<from>).*(?=<to>)' <my_file>
```

### Sed way
```bash
sed -rn 's/<from>(.*)<to>/\1/p' <my_file>
```

## Parse json from command line
Use `jq`command to parse output
Example:
```bash
curl -X GET "<url>" | jq
```

```bash
output | jq ".[].project_id"
```
