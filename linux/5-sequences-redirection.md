# Week 5: Command Sequences and Output Redirection

## Command Sequences

- **Command Sequence:** A series of commands executed sequentially, separated by semicolons.

   - `cal;pwd;date`: Executes three separate commands in order: displaying the calendar, printing the current working directory and showing the current date and time.

   - `(cal;pwd;date)`: Groups the three commands within parentheses for sequential execution, providing a single entity output.

## Output Redirection

- **Output Redirection:** Managing where command outputs are directed.

   - `cal;pwd;date > output.txt`: Redirects the output of the last command (date) to "output.txt," while displaying the calendar and current working directory in the terminal.

   - `(cal;pwd;date) > output.txt`: Redirects the grouped output of the three commands to "output.txt," including the calendar, current working directory and date and time.

   - `(cal;pwd;date) | tee output.txt`: Utilizes `tee` to both display the output in the terminal and save it to "output.txt," capturing the calendar, current working directory and date and time.

## Useful Pipelines

- **Pipelines:** Combining commands to perform more complex operations.

   - `ls -l | less`: Lists files and directories in detailed format and allows viewing output one page at a time.

   - `ls -l | grep "Aug" | wc -l`: Lists files and directories in detailed format, filters lines containing "Aug," and counts the matching lines.

   - `ls -l /bin | head -5`: Lists files and directories in detailed format in the "/bin" directory and displays only the first five lines.

## Filtering and Searching

- **Filtering and Searching:** Employing commands to search and filter results.

   - `find / -name "tempfile" | grep -v "/proc/"`: Searches for files named "tempfile" and excludes matches in the "/proc" directory.

   - `ls -l | tr 'a-z' 'A-Z'`: Lists files and directories in detailed format and converts lowercase letters to uppercase.

   - `ls -l | sort -r`: Lists files and directories in detailed format and sorts the listing in reverse order.

   - `ls -l | cut -d " " -f 2`: Lists files and directories in detailed format and extracts file/directory permissions.

   - `ls -l | grep "file" | head -5`: Lists files and directories in detailed format, filters lines containing "file," and displays the first five matching lines.

   - `ls -al | grep '^d' > directories.txt`: Lists all files and directories, filters for directories and saves the output to "directories.txt."
