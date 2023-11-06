# Week 1: Introduction to Linux

**Arguments in Linux Commands:**
- Arguments in Linux commands can be command options (e.g., -l), file pathnames (e.g., /etc) or series of characters (e.g., "Hello, world.").
- Separate arguments from a command and other arguments with whitespace (SPACE, MULTIPLE SPACES or TAB).

**Linux Commands:**
- `pwd`: Shows the current working directory.
- `ls`: Lists file names in the home directory.
- `cd /etc`: Changes the current directory to /etc.
- `ls -l`: Displays detailed metadata about files in the current directory, including last modified date, file size, ownership and permissions.
- `ls /bin`: Lists the contents of the "/bin" directory, which holds essential binary executable files and system commands.
- `clear` or `ctrl-l`: Clears the terminal screen.
- `who`: Lists users logged into the Linux server, displaying their usernames, terminal details, login time and IP addresses.
- `whoami`: Returns the current user's username.
- `w`: Displays information about currently logged-in users and their activities.

**Difference between /bin and /etc:**
- `/bin`:
   - Purpose: Contains essential binary executable files and command-line utilities.
   - Contents: Includes commonly used system commands necessary for basic system operations.

- `/etc`:
   - Purpose: Stores system configuration files.
   - Contents: Contains various configuration files that define system behavior, settings and policies.

**Difference between "who" and "whoami" commands:**
- `who`:
   - Displays information about users currently logged into the system, including usernames, terminal details, login time and IP addresses.

- `whoami`:
   - Returns the username of the current user without additional information.

**Manual Pages for Commands:**
- `man man`: Displays the manual page for the "man" command, used to access manual pages for other commands.
- `man ls`: Displays the manual page for the "ls" command, used to list files and directories.
