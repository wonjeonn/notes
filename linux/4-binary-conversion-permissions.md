# Week 4: Hexadecimal, Binary Conversion and Permissions in Linux

## Hexadecimal Number Chart

| Hexadecimal | Binary  |
|------------|---------|
| A          | 1010    |
| B          | 1011    |
| C          | 1100    |
| D          | 1101    |
| E          | 1110    |
| F          | 1111    |

## Binary to Octal Conversion

- Octal digits range from 0 to 7 and can be represented using 3 binary digits (000 to 111).

## Binary to Hexadecimal Conversion

- Hexadecimal digits range from 0 to F and can be represented using 4 binary digits (0000 to 1111).

## Changing Permissions with chmod

**Symbolic Mode:**

- Uses symbols (+, -, =) with letters (u, g, o, a) and permissions (r, w, x) to modify permissions.
- u: user/owner, g: group, o: others, a: all (u+g+o).
- r: read, w: write, x: execute.

**Absolute Mode (Octal Mode):**

- Uses numeric values to represent permissions.
- Each permission (read, write, execute) is assigned a value: read (4), write (2), execute (1).
- The sum of values represents permissions for user, group and others.

**umask:**

- Sets default permissions for newly created files and directories.
- Works as a mask that subtracts specified permissions from the default permissions.
- Default umask value is typically 022 (write permission off for group and others).
- The umask value is subtracted from base permissions (666 for files, 777 for directories) to determine final permissions.

## Examples

1. `chmod 755 file.txt`: Sets read, write and execute permissions for the owner and read-only permissions for the group and others.

2. `chmod u=rw,g=r,o=r file.txt`: Grants read and write permissions for the owner and read-only permissions for the group and others.

3. `chmod a+x script.sh`: Adds execute permission for all users.

4. `umask 0022`: Sets default file permissions as read and write for the owner and read-only for the group and others.
