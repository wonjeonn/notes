# Week 3: Pathnames and Filename Expansion

## Pathnames

- **Absolute Pathname:** Begins from the root directory (e.g., `/`) and is useful when the current directory location is unknown.

- **Relative Pathname:** Begins from the current directory and requires knowledge of the current directory's location.

## Relative Pathname Symbols

- **. (period):** Represents the current directory.

- **.. (two periods):** Represents the parent directory (e.g., one level up).

## Relative-to-Home Pathname

- Begins with the tilde character `~` to represent the user's home directory (e.g., `~/myfolder/examples`).

## Filename Expansion

- Used to match and expand filenames using special characters, including:
  - **\* (Asterisk):** Represents 0 or more characters.
  - **? (Question mark):** Represents exactly one character (any character).
  - **[ ] (Square brackets):** Represents and matches a specific character within the brackets.
  - **[!] (Square brackets with an exclamation mark):** Represents and matches an opposite character for the one enclosed in the brackets.

## Quoting Special Characters

- To use special characters as text characters in Linux commands:
  - Place `\` before the special character (e.g., `echo \* hello \*`).
  - Contain special characters within double-quotes (e.g., `echo "* hello *"`).
  - Contain special characters within single quotes (e.g., `echo '* hello *'`).

## Examples of Filename Expansion

1. `ls ???.txt`: Lists files with exactly three characters followed by `.txt`.

2. `ls ?????.txt`: Lists files with exactly four characters followed by `.txt`.

3. `ls [0-9].txt`: Lists files with a single digit followed by `.txt`.

4. `ls [0-9][0-9][0-9].txt`: Lists files with exactly three consecutive digits followed by `.txt`.

5. `ls [a-z][a-z][a-z].txt`: Lists files with exactly three lowercase alphabetic characters followed by `.txt`.

6. `ls [A-Z][A-Z][A-Z].txt`: Lists files with exactly three uppercase alphabetic characters followed by `.txt`.

7. `ls [a-zA-Z0-9][a-zA-Z0-9][a-zA-Z0-9].txt`: Lists files with exactly three alphanumeric characters followed by `.txt`.

8. `ls *.txt`: Lists all files with the `.txt` extension.

9. `ls *.[tT][xX][tT]`: Lists files with the `.txt` or `.TXT` extension.

## Echo Commands and Outputs

- `echo hello there`: Outputs "hello there".

- `echo * hello *`: Expands and outputs the list of filenames in the current directory along with "hello".

- `echo \* hello \*`: Outputs the text " * hello * ".

- `echo "* hello *"`: Outputs the text "* hello *".

- `echo '* hello *'`: Outputs the text '* hello *'.

- `echo $USER`: Outputs the username of the current user.

- `echo '* $USER *'`: Outputs the text '* $USER *'.

- `echo "* $USER *"`: Outputs the text "*USERNAME*" (where USERNAME is the actual username).
