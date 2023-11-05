# Week 8: Strings and String Functions

## 1. **Strings**

In C programming, strings are represented as arrays of characters, terminated by a null character `'\0'`.

### String Declaration and Printing

```c
#include <stdio.h>

int main() {

  char str[] = "Hello";
  printf("%s", str);

  return 0;
}
```

**Output**
```
Hello
```

## 2. **String Input**

### Example 1: Input Using `scanf`

```c
#include <stdio.h>

int main() {

  char str[20];

  printf("Enter your name: ");
  scanf("%s", str);

  printf("%s", str);

  return 0;
}
```

**Output**
```
Enter your name: Hello World
Hello
```

### Example 2: Input Using `fgets`

```c
#include <stdio.h>

int main() {

  char str[20];

  printf("Enter your name: ");
  fgets(str, sizeof(str), stdin);

  printf("%s", str);

  return 0;
}
```

**Output**
```
Enter your name: Hello World
Hello World
```

## 3. **String Characters**

### Accessing and Modifying Characters

```c
#include <stdio.h>

int main() {

  char str[] = "Hello";

  printf("%c\n", str[0]);
  printf("%c\n", str[1]);
  printf("%c\n", str[2]);
  printf("%c\n", str[3]);
  printf("%c", str[4]);

  return 0;
}
```

**Output**
```
H
e
l
l
o
```

### Changing Characters in a String

```c
#include <stdio.h>

int main() {
  char str[] = "Hello";

  str[0] = 'h';
  str[2] = 'L';

  printf("%s", str);

  return 0;
}
```

**Output**
```
heLlo
```

## 4. **String Functions**

### `strlen()` Function

#### Example 1: Finding String Length

```c
#include <stdio.h>
#include <string.h>

int main() {

  char str[] = "Hello World";
  
  printf("%s\n", str);
  printf("Length: %zu", strlen(str));

  return 0;
}
```

**Output**
```
Hello World
Length: 11
```

#### Example 2: Comparing String Lengths

```c
#include <stdio.h>
#include <string.h>

int main() {

  char str1[20];
  char str2[20];
  
  printf("Enter first word: ");
  fgets(str1, sizeof(str1), stdin);
  printf("Enter second word: ");
  fgets(str2, sizeof(str2), stdin);
  
  if (strlen(str1) > strlen(str2)) {
      printf("Longest word: %s", str1);
  }
  else if (strlen(str1) == strlen(str2)) {
      printf("Same word length");
  }
  else {
      printf("Longest word: %s", str2);
  }
  
  return 0;
}
```

**Output**
```
Enter first word: C
Enter second word: Programming
Longest word: Programming
```

### `strcpy()` Function

```c
#include <stdio.h>
#include <string.h>

int main() {
  
  char str1[20];
  char str2[20] = "Hello";

  strcpy(str1, str2);

  printf("%s", str1);

  return 0;
}
```

**Output**
```
Hello
```

### `strcat()` Function

```c
#include <stdio.h>
#include <string.h>

int main() {

  char str1[20] = "Hello, ";
  char str2[20] = "World!";
  
  strcat(str1, str2);

  printf("%s", str1);

  return 0;
}
```

**Output**
```
Hello, World!
```

### `strcmp()` Function

```c
#include <stdio.h>
#include <string.h>

int main() {

  char str1[] = "abcd";
  char str2[] = "cdef";
  
  int result = strcmp(str1, str2);

  printf("%d", result);

  return 0;
}
```

**Output**
```
-2
```
