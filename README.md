# Compiler-Project

This repository includes a compiler implemented in C, developed according to specifications in *Language Specifications.pdf*. The project was created as part of the *Compiler Construction* course at Jamia Hamdard.

This compiler processes input files based on defined language rules, and if the input meets the syntax and semantics, it generates assembly-level code. Sample test cases are available in the *Compiler/testcases* directory.

The compiler is designed to run on GCC version 5.4.0 and has been tested on Ubuntu 16.04. Windows users can run the code using [Cygwin](https://www.cygwin.com/).

### Building the Compiler
1. Navigate to the *Compiler* directory: `cd Compiler`
2. Build the project by running `make`
3. This creates an executable named *compiler*

### Running a Test Case on the Compiler
1. Ensure the *compiler* executable is in the current directory
2. Use the command `./compiler <RELATIVE_PATH_TO_TESTCASE_FILE> <NAME_OF_ASM_FILE>`
3. Choose from 11 available testing options to explore different features
4. Select option 10 to produce assembly code; option 0 exits the program (using Ctrl + C leaves the ASM file empty)
5. To run the generated assembly code, use `nasm -felf64 code.asm && gcc code.o && ./a.out` (assuming *code.asm* is the generated file name)

### Compilation Stages (Option 10)
| Stage               | Description                                                                                         |
|---------------------|-----------------------------------------------------------------------------------------------------|
| Lexical Analysis    | Classifies input file content into tokens as per language rules                                     |
| Syntax Analysis     | Builds a Parse Tree from the tokens; the process halts if there are syntax errors                   |
| Semantic Analysis   | Creates an Abstract Syntax Tree, updates the Symbol Table, and halts on semantic errors             |
| Code Generation     | Produces assembly code; restricted to single-function cases (main) that handle integers only        |