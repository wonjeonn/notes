# Week 8: Regular Expressions (Regex)

## Literal (Simple) Regular Expressions

- Simple regular expressions match normal characters exactly as they appear.

## Complex Regular Expressions

- Use special symbols for precise pattern matching.
- Common symbols: ^, $, ., [], *, |.

### Complex Regular Expressions Examples

**Anchors:**

- `^`: Matches lines that begin with a specific pattern.
- `$`: Matches lines that end with a specific pattern.

**Single Character:**

- `.`: Represents any single character.

**Character Class:**

- `[]`: Matches a single character from a defined set.
- `[^]`: Matches a single character NOT in the defined set.

**Zero or More Occurrence:**

- `*`: Matches zero or more occurrences of the preceding character.

### Extended Regular Expressions with `egrep` or `grep -E`

**1. Repetition:**

- `{min,max}`: Specifies min and max repetitions.

**2. Groups:**

- `( )`: Encloses a group for repetition or other operations.

**3. Or condition:**

- `|`: Matches any of the alternatives specified.

### Extended Regular Expression Examples

#### Repetition:

- `egrep "^[0-9]{1,}$" data.txt`: Matches lines with one or more digits.

#### Groups:

- `egrep "(the ){2,}" data.txt`: Matches lines with "the" repeated at least twice.

#### Or condition:

- `egrep "(lazy fox ){2,3}" data.txt`: Matches lines with "lazy fox" repeated 2 to 3 times.
- `egrep "(this|that) {1,}" data.txt`: Matches lines with "this" or "that" at least once.
- `egrep "(a|b|c) {3,}" data.txt`: Matches lines with "a," "b," or "c" repeated at least three times.

## Searching with Regular Expressions

- `grep`: Searches for patterns in text.
- `grep -i`: Performs a case-insensitive search.

### Word Boundary Search

- `grep -w -i "the" textfile1.txt`: Matches the word "the" with word boundaries.

### Anchoring

- `grep -w -i "^the" textfile1.txt`: Matches lines starting with "the."
- `grep -w -i "the$" textfile1.txt`: Matches lines ending with "the."
- `grep -w -i "^the$" textfile1.txt`: Matches lines consisting solely of "the."

### Complex Regular Expressions

- `grep "^..." textfile1.txt`: Matches lines starting with any three characters.
- `grep "^...$" textfile1.txt`: Matches lines consisting of exactly three characters.
- `grep "^[0-9][0-9][0-9]$" textfile1.txt`: Matches lines with exactly three digits.
- `grep "[A-Z][A-Z][A-Z]$" textfile1.txt`: Matches lines ending with three uppercase letters.
- `grep "^[0-9][0-9][0-9]$" textfile1.txt`: Matches lines consisting of exactly three digits.
- `grep "^[a-zA-Z0-9][a-zA-Z0-9][a-zA-Z0-9]$" textfile1.txt`: Matches lines consisting of exactly three alphanumeric characters.

### Using the "*" Symbol

- `grep "x*" textfile1.txt`: Matches zero or more occurrences of the letter "x."
- `grep "xx*" textfile1.txt`: Matches strings with more than one occurrence of the letter "x."

### Combining Anchors and ".*" Symbol

- `grep "^[0-9].*[0-9]$" textfile1.txt`: Matches strings that begin and end with a number with anything in between.
- `grep "^[A-Z].*X.*[0-9]$" textfile1.txt`: Matches strings with a capital letter at the beginning, a capital "X" somewhere in between and a number at the end.

### Using Extended Regular Expression Symbols

- `egrep "^[+-]{0,1}[0-9]{1,}$" numbers2.dat`: Matches signed or unsigned integers using extended regular expression symbols.

## Handling Files and Patterns

- `tee`: Redirects output to a file while displaying it on the screen.
- `cp`: Copies files.
- `ls`: Lists files and directories.

## Searching and Replacing with Regular Expressions

- `vi`: A text editor with search and replace capabilities.
- `:s`: The substitute command in vi for search and replace.
