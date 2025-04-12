# Java Cipher Project

![Java](https://img.shields.io/badge/Java-17-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Project Overview

This project is a Java implementation of a block cipher encryption and decryption tool, developed as part of a university assignment (Project 1) by Fengkai Liu and Yu Liu at the University of Rochester. The program allows users to encrypt or decrypt text files using a 56-bit secret key, implementing a custom Feistel network with key scheduling, S-box substitution, and permutation techniques. It demonstrates proficiency in Java programming, file I/O operations, and cryptographic algorithm design.

**Note**: Despite the query mentioning "Java Black Jack," the provided source code is for a cipher project. This README reflects the actual cipher implementation.

## Features

- **Encryption and Decryption**: Supports both encryption and decryption of text files using a custom block cipher algorithm.
- **Feistel Network**: Implements a 10-round Feistel structure with key scheduling for secure transformations.
- **User Interaction**: Provides a command-line interface for selecting encryption/decryption, input/output file paths, and secret key entry.
- **File Handling**: Reads input from and writes output to text files, with flexible path support (relative or absolute).
- **Binary Processing**: Converts text to binary, processes it in 64-bit blocks, and handles padding appropriately.
- **Built-in Tests**: Includes test cases to verify the correctness of encryption and decryption functions.

## Installation

To run this project, you need Java installed on your machine. The project is compatible with Java 17 or later.

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/java-cipher.git
   ```
2. **Navigate to the Project Directory**:
  ```bash
  cd java-cipher
  ```
3. **Compile the Java File**:
  ```bash
  javac -d bin src/Cipher.java
  ```
4. **Run the Application**:
  ```bash
  java -cp bin Cipher
  ```

## Usage
After compiling and running the application, follow the command-line prompts to encrypt or decrypt a file:
- **Choose Operation**: Enter `E` to encrypt or `D` to decrypt.
- **Specify File Location**: Indicate whether the input file is in the `src` directory (`Y`/`N`), then provide the file name or path.
- **Enter Secret Key**: Input a 56-digit binary key (e.g., a string of 56 `0`s and `1`s).
- **Specify Output File**: Provide the name for the output file.
- **For Decryption**: Specify whether the output should be text (`T`) or a binary string (`B`).

## Example Usage
### Encryption
```text
Do you want to encrypt or decrypt (E/D): E
Are your file and this program both in a src directory? (Y/N): Y
Notice: you can enter the ".txt" at the end of the file name but it's not necessary.
File name: input
Secret key: 11111111111111111111111111111111111111111111111111111111
Notice: you can enter the ".txt" at the end of the file name but it's not necessary.
Output file name: encrypted_output
File encrypted and saved successfully.
```

### Decryption (Text Output)
```text
Do you want to encrypt or decrypt (E/D): D
Are your file and this program both in a src directory? (Y/N): Y
Notice: you can enter the ".txt" at the end of the file name but it's not necessary.
File name: encrypted_output
Secret key: 11111111111111111111111111111111111111111111111111111111
Notice: you can enter the ".txt" at the end of the file name but it's not necessary.
Output file name: decrypted_output
Enter 'T' for text data or 'B' for binary string data: T
File decrypted and saved successfully.
```

## Code Structure
The project consists of a single `Cipher.java` file with multiple static methods organized to handle different aspects of the cipher:
- Main Method: Entry point, manages user input, file operations, and program flow.
- Encryption/Decryption:
  - `encryption`: Converts input to binary, divides into blocks, and encrypts.
  - `decryptBlock`: Decrypts individual 64-bit blocks using the Feistel network.
  - `encryptBlock`: Encrypts individual 64-bit blocks.
- Core Functions:
  - `functionF`: Applies the Feistel function (XOR, S-box substitution, permutation).
  - `keyScheduleTransform`: Generates 10 round sub-keys from the 56-bit key.
  - `substitutionS`: Performs S-box substitution on 8-bit segments.
  - `permuteIt`: Applies a fixed permutation to 32-bit data.
- Utility Methods:
  - `toBinaryString`: Converts text to binary.
  - `divideDataIntoBlocks`: Splits binary data into 64-bit blocks.
  - `xorIt`: Performs bitwise XOR on binary strings.
  - `shiftIt`: Left-shifts binary strings for key scheduling.
  - `getFileContent`: Reads file content into a string.
- Testing: `runTests`: Executes predefined test cases to verify functionality.

## Simplified Flow Diagram

```text
graph TD
    A[Main] --> B[User Input]
    B --> C[File Reading]
    C --> D[Encryption/Decryption]
    D --> E[Key Scheduling]
    E --> F[Feistel Rounds]
    F --> G[File Writing]
    A --> H[Run Tests]
```
## Testing

The project includes a `runTests` method that executes predefined test cases on startup to validate the encryption and decryption logic. These tests cover various input scenarios (e.g., all ones, all zeros, specific blocks) and print the results to the console.

### Running Tests
Tests run automatically when you execute the program:

```bash
java -cp bin Cipher
```

### Sample Test Output
```text
Output for: encryption(all ones, all ones)
0101011010001110111001000111100001001110010001100110000011110101

Output for: encryption(all zeros, all ones)
1100111010001000100011011010110110110010100101011001100000101000

[...]
```

To extend testing, consider integrating JUnit for more comprehensive unit tests (not included in the current codebase).

### License
This project is licensed under the MIT License. See the  file for details.
