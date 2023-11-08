# Week 7: File Stream Classes in C++

## File I/O

- `std::ifstream`: Used for processing input from a file stream.
- `std::ofstream`: Used for processing output to a file stream.
- `std::fstream`: Used for processing both input and output on a file stream.

## File Stream Operations

- To work with files, include the `<fstream>` header and create file objects:

  ```cpp
  #include <fstream>

  int main() {
      std::ifstream fin("input.txt"); // For reading from input.txt
      // ...

      std::ofstream fout("output.txt"); // For writing to output.txt
      // ...
  }
  ```

- To confirm if a file is open, use the `is_open()` member function:

  ```cpp
  #include <fstream>

  std::ofstream fout("output.txt");

  if (!fout.is_open()) {
      std::cerr << "File is not open" << std::endl;
  } else {
      // File is open
      // ...
  }
  ```

## Opening Files

Example of opening files:

  ```cpp
  #include <fstream>

  std::ofstream outFile("output.txt"); // Opens for writing
  std::ifstream inFile("input.txt");   // Opens for reading
  std::fstream file("data.txt", std::ios::in | std::ios::out); // Opens for both reading and writing
  ```

## Writing to Files

To write to a file, use the `<<` operator similarly to `cout`:

  ```cpp
  std::ofstream outFile("output.txt");
  outFile << "Hello, File!";
  outFile.close();
  ```

## Reading from Files

To read from a file, use the `>>` operator similarly to `cin`:

  ```cpp
  std::ifstream inFile("input.txt");
  int number;
  inFile >> number;
  ```

## Combining Reading and Writing

Read from and write to the same file using an `fstream` object:

  ```cpp
  std::fstream file("data.txt", std::ios::in | std::ios::out);
  file << "Writing to the file";
  file.seekg(0); // Move the read/write pointer to the beginning of the file
  std::string data;
  file >> data; // Reads from the file
  ```

## File Stream Modes

- **`std::ios::in`**: Open for reading.
- **`std::ios::out`**: Open for writing.
- **`std::ios::trunc`**: Truncate the file if it exists.
- **`std::ios::app`**: Append to the end of the file.
- **`std::ios::ate`**: Set the initial position at the end of the file.

## Rewinding a File

- **`seekg(pos)`**: Sets the read pointer to the specified position.
- **`seekp(pos)`**: Sets the write pointer to the specified position.

## Logical Negation Operator for File Streams

The logical negation operator `!` can be used to check the state of file stream objects.

  ```cpp
  std::ifstream inFile("input.txt");
  if (!inFile) {
      std::cerr << "Error opening file!";
  }
  ```

## Reading and Writing Custom Types

When reading/writing custom objects, overload `<<` and `>>` operators for these objects and handle the serialization and deserialization process manually.

  ```cpp
  std::ofstream outFile("output.txt");
  CustomObject obj;
  outFile << obj; // Assuming << operator is overloaded for CustomObject

  std::ifstream inFile("input.txt");
  CustomObject obj;
  inFile >> obj; // Assuming >> operator is overloaded for CustomObject
  ```

## Concatenating Files

Data from `file1.txt` and `file2.txt` are concatenated and stored in `output.txt`.

  ```cpp
  #include <fstream>

  int main() {
      std::ifstream inFile1("file1.txt");
      std::ifstream inFile2("file2.txt");
      std::ofstream outFile("output.txt");

      char c;
      while (inFile1.get(c)) {
          outFile.put(c);
      }

      while (inFile2.get(c)) {
          outFile.put(c);
      }

      inFile1.close();
      inFile2.close();
      outFile.close();
  }
  ```

## Reading and Writing Custom Types to Files

`<<` and `>>` operators are overloaded for the `CustomObject` class, allowing objects of this class to be read from and written to files.

  ```cpp
  class CustomObject {
      // Definition of the class

      friend std::ostream& operator<<(std::ostream& os, const CustomObject& obj);
      friend std::istream& operator>>(std::istream& is, CustomObject& obj);
  };

  std::ostream& operator<<(std::ostream& os, const CustomObject& obj) {
      // Serialization logic for CustomObject
      return os;
  }

  std::istream& operator>>(std::istream& is, CustomObject& obj) {
      // Deserialization logic for CustomObject
      return is;
  }

  int main() {
      std::ofstream outFile("output.txt");
      CustomObject obj;
      outFile << obj;

      std::ifstream inFile("input.txt");
      inFile >> obj;
  }
  ```