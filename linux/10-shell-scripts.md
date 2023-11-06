# Week 10: Shell Scripts

## Using a Shebang Line

- Use a shebang line at the beginning of the script.
- Shebang line specifies the shell to run the script.
- Example: `#!/bin/bash`

## Setting Permissions / Running Shell Scripts

- Assign execute permissions for the user: `chmod u+x filename`
- Execute the shell script:
  - Relative path: `./filename`
  - Absolute path: `/path/to/filename`
  - Relative-to-home path: `~/filename`

## Variables

### Environment Variables

- Environment variables shape the working environment.
- Display variables: `set | more`
- Use `$` before variable name to expand its value.

**Examples:**

- `echo $PWD`
- `echo $PATH`
- `echo $USER`

### User Defined Variables

- Define custom variables with an equal sign: `name="Murray Saul"`
- Use `read` to prompt the user for variable value.
- `readonly` command prevents variable changes.

## Positional Parameters

- `$1`, `$2`, `$3`, ... represent arguments.
- `$0` refers to the script or shell name.
- Use braces for numbers > 9: `${10}`, `${23}`.
- Shift parameters with `shift`.

**Examples:**

- `echo $1`
- `echo $2`
- `echo ${10}`

## Special Parameters

- `$#` - Number of arguments.
- `$*`, `$@` - All arguments as a single string or individually.
- `$?` - Exit status of the last command.

**Examples:**

- `echo $#`
- `echo $*`

## Command Substitution

- Run a command within another using `$(command)`.
- Example: `echo $(pwd)`

## Math Operations

- Use double parentheses for math operations: `$(( ))`.
- Operators: `+`, `-`, `*`, `/`, `%`, `**`, `++`, `--`.

**Examples:**

```bash
num1=5; num2=10
echo $(($num1 + $num2))
```

## Control Flow Statements

- Use condition tests to get TRUE (0) or FALSE (non-zero).
- Run the command to get the exit status or use the `test` command.
- Examples: `-lt` (<), `-le` (<=), `-gt` (>), `-ge` (>=), `-eq` (=), `-ne` (!=)

**Examples:**

- `test $num1 -eq $num2`
- `test $num1 -lt $num2`

## Logic Statements

- Use `if` statements to execute commands based on conditions.

**Example:**

```bash
if [ $num1 -lt $num2 ]
then
  echo "Less Than"
fi
```

**if-else Statement**

- Use `if-else` for different actions based on a condition.

**Example:**

```bash
if [ $num1 -lt $num2 ]
then
  echo "Less Than"
else
  echo "Greater Than or Equal To"
fi
```

## Loop Statements

- Use loops to execute a sequence of commands repeatedly.
- `for item in list; do ... done`

**Example:**

```bash
for x in apples oranges bananas
do
  echo "The item is: $x"
done
```

**Shell Scripting: If-Elif-Else Statements**
- The `elif` statement allows for additional conditional tests when the previous one is FALSE, providing adaptability.
- If the `if` condition is TRUE, it executes the commands between `if` and `elif`. If FALSE, it proceeds to the `elif` condition.
- Multiple `elif` statements can be used for further testing.
- If neither `if` nor `elif` conditions are TRUE, the commands under `else` execute.

**Example of If-Elif-Else Statement:**
```bash
num1=5
num2=10
if test $num1 -lt $num2
then
  echo "Less Than"
elif test $num1 -gt $num2
then
  echo "Greater Than"
else
  echo "Equal to"
fi
```

**For Loop Using Command Substitution**
- A for loop with command substitution iterates over items from the output of a command (e.g., `$(ls)`).
- It assigns each item to a variable for processing in the loop.

**Example of For Loop with Command Substitution:**
```bash
for x in $(ls)
do
  echo "The item is: $x"
done
```

**While Loop**
- A while loop repeatedly executes a block of code while a condition is TRUE.
- It continues execution until the condition becomes FALSE.

**Example of While Loop (with user input):**
```bash
answer=10
read -p "Pick a number between 1 and 10: " guess
while test $guess -eq 10
do
  read -p "Try again: " guess
done
echo "You are correct"
```

**Example of While Loop (counting):**
```bash
value=1
while [ $value -le 5 ]
do
  echo "$value"
  ((value=value+1)) # Alternatively, use ((value++))
done
```

**Exit & Break Statements**
- The `exit` statement terminates a shell script and provides an exit status code.
- The `break` statement terminates a loop and allows the script to continue running.

**Example of Exit Statement:**
```bash
if [ $# -ne 1 ]
then
  echo "USAGE: $0 [arg]"
  exit 1
fi
```

**Example of Break Statement:**
```bash
read -p "Enter a number: " number
while [ $number -ne 5 ]
do
  read -p "Try again. Enter a number: " number
  if [ $number -eq 5 ]
  then
    break
  fi
done
```

**Start-Up Files**
- Shell start-up files are scripts that run during login, logout or when starting a new shell.
- System-wide start-up files include `/etc/profile`.
- User-specific start-up files include `~/.bash_profile` (login) and `~/.bashrc` (interactive shell).

**Logout Files**
- Logout start-up files in the user's home directory, like `~/.bash_logout`, reset or restore the shell environment upon logout.
