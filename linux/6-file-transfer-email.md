# Week 6: File Transfer and Email Commands

## File Transfer

### Secure Copy Protocol (scp)

- **Copying a File to Remote Server:**
  ```shell
  scp mytext.txt user1@tech.myserver.com:~
  ```

- **Copying and Renaming a File on Remote Server:**
  ```shell
  scp mytext.txt user1@tech.myserver.com:~/yourtext.txt
  ```

- **Copying a Local File to Remote Server:**
  ```shell
  scp ~/project/linux.txt yourusername@linux.techie.org:~
  ```

### Secure File Transfer Protocol (sftp)

- **Connecting to a Remote Server:**
  ```shell
  sftp username@server-address
  ```

- **Displaying Current Local Directory:**
  ```shell
  lpwd
  ```

- **Listing Local Files and Directories:**
  ```shell
  lls
  ```

- **Listing Remote Files and Directories:**
  ```shell
  ls
  ```

- **Downloading a File from Remote Server:**
  ```shell
  get answers.txt
  ```

- **Uploading a File to Remote Server:**
  ```shell
  put questions.txt ~/documents/tests/
  ```

- **Quitting sftp Session:**
  ```shell
  quit
  ```

## Email

- **Sending an Email with Attachment:**
  ```shell
  mail -s "Subject" recipient@example.com < file.txt
  ```

- **Linux Commands for File Transfer and Email:**

    | Command | Options | Purpose                                      |
    |---------|---------|----------------------------------------------|
    | `scp`   | `-r`    | Copy files and directories recursively        |
    |         | `-p`    | Preserve file attributes                      |
    |         | `-q`    | Quiet mode (suppress progress meter)          |
    | `sftp`  | `-P`    | Specify port number for the SSH connection    |
    |         | `-b`    | Batch mode (read commands from a file)        |
    |         | `-v`    | Verbose mode (display detailed information)   |
    | `mail`  | `-s`    | Specify the subject line of the email         |
    |         | `-a`    | Attach a file to the email                    |
    |         | `-c`    | Specify carbon copy recipients                |
    |         | `-b`    | Specify blind carbon copy recipients          |

- **Common sftp Commands:**

    | Command  | Purpose                                           |
    |---------  |---------------------------------------------------|
    | `ls`      | List files and directories in the current directory|
    | `cd`      | Change directory                                  |
    | `pwd`     | Print current working directory                   |
    | `get`     | Download a file from the remote server            |
    | `put`     | Upload a file to the remote server                 |
    | `rm`      | Remove a file from the remote server               |
    | `mkdir`   | Create a directory on the remote server            |
    | `rmdir`   | Remove a directory from the remote server          |
    | `quit`    | Quit the sftp session                             |
