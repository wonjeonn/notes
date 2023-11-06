# Week 7: Unix/Linux File Systems, Processes, Aliases and Command History

## I-Node (Index Node) and File Identification

- **I-Node:** A data structure storing metadata about a file in Unix/Linux systems.
- **Unique Identifier:** Each file has a distinct I-node number, serving as its unique identifier.
- **Information Stored:** I-node contains details such as file type, ownership, permissions, timestamps and data block location.
- **Displaying I-Node:** Use `ls -i` or `ls -li` to view file details along with the I-node number.

## Hard Links

- **Definition:** Hard links allow multiple filenames to point to the same data or I-node.
- **Shared I-Node:** All hard links share the same I-node number, indicating shared data.
- **Creation:** Use `ln` command to create hard links, creating multiple directory entries for the same file.
- **Editing:** Changes made in one hard link are reflected in others and the original file.
- **Deletion:** Deleting a hard link retains data if other links or the original file exist.
- **Limitation:** Cannot cross file system boundaries or point to directories.

## Symbolic Links (Soft Links)

- **Definition:** Symbolic links point to another file or directory by storing the target file's path/location.
- **I-Node:** Symbolic links have their own I-node and contain the path to the target file.
- **Creation:** Use `ln -s` command to create symbolic links.
- **Accessing:** Accessing a symbolic link reads the target path and follows to the actual file.
- **Breakage:** If the target file is moved or deleted, the symbolic link becomes a "broken link."
- **Usage:** Can point to files or directories within the same or different file systems.

## Managing Processes

- **Process:** A running program or command in Unix/Linux identified by a unique Process ID (PID).
- **Terminal Processes:** Terminal has foreground (current session) and background processes.
- **Commands:** Use `ps`, `top`, `jobs`, `kill` to manage processes.
- **Foreground Control:**
  - `Ctrl-C`: Sends SIGINT to terminate the foreground process.
  - `Ctrl-Z`: Suspends the process, sending it to the background.
  - `fg`: Brings a background process to the foreground.
- **Background Control:**
  - `bg`: Runs the most recent process in the background.
  - `jobs`: Lists background job status.
- **Termination:**
  - `kill`: Sends signals to terminate processes using PID or job number.

## Aliases

- **Definition:** Aliases are custom command shortcuts, modifying or simplifying existing command behavior.
- **Creation:** Aliases are created or modified in memory/session or startup files like `~/.bashrc`.
- **Commands:**
  - `alias`: Lists existing aliases.
  - `alias alias-name='command'`: Creates aliases for complex or frequently used commands.
  - `unalias alias-name`: Removes an alias.

## Command History

- **History:** Maintains a list of previously executed commands.
- **File:** `~/.bash_history` stores command history.
- **Navigation:** Use up/down arrows to navigate history.
- **Commands:**
  - `history`: Displays command history.
  - `!!`: Re-executes the last command.
  - `!num`: Reruns a specific command by number.
  - `!prefix`: Executes the most recent command starting with "prefix."
