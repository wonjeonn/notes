# Week 11: File Input/Output in C

## 1. **File Basics**

### Writing to a File

```c
#include <stdio.h>

int main() {

  FILE* filePointer;

  filePointer = fopen("output.txt", "w");

  if (filePointer == NULL) {
    printf("File could not be opened.");
  } else {
    fprintf(filePointer, "Hello, World!");
    printf("Data written to the file successfully.");
    fclose(filePointer);
  }

  return 0;
}
```

### Reading from a File

```c
#include <stdio.h>

int main() {

  FILE* filePointer;
  char buffer[100];

  filePointer = fopen("input.txt", "r");

  if (filePointer == NULL) {
    printf("File could not be opened.");
  } else {
    fscanf(filePointer, "%s", buffer);
    printf("Data from the file: %s", buffer);
    fclose(filePointer);
  }

  return 0;
}
```

## 2. **Reading and Writing Structures to a File**

### Writing Structures to a File

```c
#include <stdio.h>

struct Person {
  char name[50];
  int age;
};

int main() {

  FILE* filePointer;
  struct Person person = {"Alice", 30};

  filePointer = fopen("person_info.txt", "wb");

  if (filePointer == NULL) {
    printf("File could not be opened.");
  } else {
    fwrite(&person, sizeof(struct Person), 1, filePointer);
    printf("Data written to the file successfully.");
    fclose(filePointer);
  }

  return 0;
}
```

### Reading Structures from a File

```c
#include <stdio.h>

struct Person {
  char name[50];
  int age;
};

int main() {

  FILE* filePointer;
  struct Person person;

  filePointer = fopen("person_info.txt", "rb");

  if (filePointer == NULL) {
    printf("File could not be opened.");
  } else {
    fread(&person, sizeof(struct Person), 1, filePointer);
    printf("Name: %s\n", person.name);
    printf("Age: %d", person.age);
    fclose(filePointer);
  }

  return 0;
}
```
