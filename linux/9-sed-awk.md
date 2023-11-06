# Week 9: Sed and Awk

## Sed (Stream Editor)

- **Usage:**
  ```
  sed [-n] 'address instruction' filename
  ```

- **Address:**
  - Specifies lines to apply instructions to.
  - Line numbers, ranges and regular expressions can be used.
  - No address applies instruction to ALL lines.

- **Instructions:**
  1. `p` - Print: Print lines that match the address.
  2. `d` - Delete: Delete lines that match the address.
  3. `q` - Quit: Stop processing after the first match.
  4. `s` - Substitute: Replace matched pattern with a replacement.

### Sed Examples

- Substitute "TUTORIAL" with "LESSON" in `data.txt`:
  ```
  sed 's/TUTORIAL/LESSON/g' data.txt
  ```

## Awk

- **Usage:**
  ```
  awk [-F] 'selection-criteria {action}' file-name
  ```

- **Selection Criteria:**
  - Regular expressions, numeric/string comparisons, built-in variables.
  - Combining patterns with `&&` (AND) and `||` (OR).

- **Action:**
  - Commands within braces `{}` applied to matching lines.
  - `$0`, `$1`, `$2`, ..., `${10}`, `${11}`, etc. represent fields.
  - Built-in variables like `NR` (record number) can be used.

### Awk Examples

- Display lines where the first field matches a specific pattern:
   ```
   awk '$1 ~ /pattern/' filename
   ```

- Display lines where the first field starts with a digit (0 to 9):
   ```
   awk '$1 ~ /^[0-9]/' filename
   ```

- Display lines where the second field does not match a specific pattern:
   ```
   awk '$2 !~ /line/' filename
   ```

- Display lines where the third field is greater than 50 and the fourth field is less than or equal to 100:
   ```
   awk '$3 > 50 && $4 <= 100' filename
   ```

- Display lines where the first field matches a pattern and the third field is greater than 50:
   ```
   awk '$1 ~ /pattern/ && $3 > 50' filename
   ```

- Display lines where either the first field matches a pattern or the second field contains a keyword:
   ```
   awk '$1 ~ /pattern/ || $2 ~ /keyword/' filename
   ```

- Display the first five lines of the file:
   ```
   awk 'NR >= 1 && NR <= 5' filename
   ```
