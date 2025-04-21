---
title: Shell Scripting Primer
parent: Coding Resources
nav_enabled: true 
---

# Shell Scripting Primer

Date: December 13, 2023 3:05 PM

Course: [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/) by MIT 

[The Missing Semester of Your CS Education](https://missing.csail.mit.edu/)

<aside>
📅  Course

- [x]  [Course overview + the shell](https://missing.csail.mit.edu/2020/course-shell/)
- [x]  [Shell Tools and Scripting](https://missing.csail.mit.edu/2020/shell-tools/)

[Github Primer](https://www.notion.so/Github-Primer-d3686c7bfac9415a9318b17f8bd82439?pvs=21)

</aside>

### [Lecture 1: The Shell](https://missing.csail.mit.edu/2020/course-shell/)

BASH = default language

argument = separated by space (not parenthesis) — if you put a space, it will indicate an argument

**Actions**

help functions

‘**fn’ - -help**    - add this to a command and it will tell you what the function is

**man ‘fn’** - will open the manual page for that function (more readable than - -help)

Setting outputs as values “<”:

`y < x` 

- sets the value of y as the content of x

cat < y

- prints the value of y

cat < y > x

- sets the value of y as the contents of x

y > x

y > x

- sets y as the value of x, and then again

y >> x

y >> x

- y is now the value of x appended to the output of x

Setting output as input, “|”:

*sentence* | `count_letters`

- this would take the sentence stored in the

Common Shell Commands
`./` = current directory

`..` = parent directory

**`pwd`=** print working dir

**`cd /'dir'` =** change wd to specified dir

**`cd ..`** = change wd to parent directory

**`cd -`** = will go back to the directory you were last in 

**`ls`** = prints all the files in current dir

**`echo`** = returns whatever is after echo (or in quotes for stuff w spaces in it)

**`cat`** = display contents of files, concatenate (if multiple listed)

**`vim`** or `vi` = displays contents, like cat, but with additional features (scrolling, etc.)

`:q` gets you out of the vim viewer

**`cat ‘file’` =** prints the contents of a file

**`xdg-open** ‘file’` = 

**`~`** = home directory

**`<fn> -l`** = will give you more info on that function

**`ls -l`** = returns the permissions you have on the working directory
**`chmod +x <script.sh`>** = gives execute permissions to script.sh 

**`chmod ugo+rwx <script.sh`>** = change your permissions in a folder to read-write-execute 

**`mv /dir` =** moves a file

**`mkdir`** = make a new directory

**`rm`** = remove file (theres no undo)

**`cp`** 
`rsync [options] <source_file> <destination_directory>` = copy files; [options]: These are optional flags that modify the behavior of `rsync`. Some common options include `-a` (archive mode, preserves permissions and other attributes), `-v` (verbose output), `-r` (recursively copy directories), and `-u` (update only, skip files that are newer in the destination).

- rsync is recommended for larger files

**`>`** = specifies where you want the output of that command to be saved/to go

**`x | y`** = makes the *output* of x the *input* of 

**`sudo`** = runs the next command as the Root / Super User (can’t run multiple commands w/o shell) 

- `sudo su` = run root as shell
- dangerous

**`tee`** = takes its input, and writes it to a (specific?) file, and prints it out

**`tail`** = print __ of the last output

**`tail -n1`** = print the last 1 line of the last output

**`./script.sh`** = will run script.sh in current directory

**`python script.py`** = run script.py in python

### [Lecture 2: Shell Tools and Scripting](https://missing.csail.mit.edu/2020/shell-tools/)

Common Errors

`foo = bar`  = error, because there are spaces between words foo“ “=” “bar

`echo ‘Hello $foo’` → Hello $foo

because single quotes define strings and don’t read variables as variables

Assigning Variables

=, ie foo=bar

Defining Functions

‘fn’ () {

defined function

}

**`foo=bar**`   = sets foo to the value of bar

**`echo “Hello $foo”**` → Hello bar

`source ‘fn’.sh` = define the function fn, from the shell file, now its in your prog mem

- now ‘`fn`' can be called directly

**`$_`** = replaces $_ with the last used argument

`!!` = replaces !! with the last line you ran

`grep ‘x’ ‘file’`= searches for ‘x’ in ‘file’

`x || y` = or 

<aside>
🌄 **$** in BASH

In Bash, the dollar sign ($) has various meanings depending on its context. Here are some common uses:

1. **Variable substitution:** When followed by a variable name, the dollar sign is used to substitute the value of that variable. For example:
- `my_variable="Hello"
echo $my_variable`
    
    This would print "Hello" because the value of the variable `my_variable` is substituted in the `echo` command.
    
- **Command substitution:** The dollar sign, when followed by parentheses, is used to execute a command and substitute its output. For example:
- `current_date=$(date)
echo "Current date is: $current_date"`
    
    This would execute the `date` command, capture its output, and store it in the variable `current_date`, which is then used in the `echo` command.
    
- **Special variables:** Some special variables in Bash also use the dollar sign. For instance, `$0` refers to the name of the script or shell, and `$1`, `$2`, etc., refer to the positional parameters passed to a script or function.
- `echo "Script name: $0"
echo "First parameter: $1"`
    
    If you run the script with parameters (`./myscript.sh param1`), it would print the script name and the first parameter.
    
- **Arithmetic operations:** Inside double parentheses, the dollar sign can be used for arithmetic operations:
1. `result=$((5 + 3))
echo "Result: $result"`
    
    This would calculate the sum of 5 and 3 and store it in the variable `result`, which is then echoed.
    

Remember that the context in which the dollar sign is used determines its meaning, so its function can vary based on the situation in your Bash script.

</aside>

###