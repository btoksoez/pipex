# Pipex
The purpose of this project is to delve into the details of UNIX mechanisms, specifically pipes and process management.

![pipex](./img/pipex.jpg)

## Introduction
The pipex program replicates the behavior of the following shell command:
```
$> < file1 cmd1 | cmd2 > file2
```
And it can be used as follows:
```
$> ./pipex file1 cmd1 cmd2 file2
```
file1 and file2 are file names.
cmd1 and cmd2 are shell commands with their parameters.
The program should handle all errors, including incorrect commands, file permissions, and more.

## Examples

### Example 1:
```
$> ./pipex infile "ls -l" "wc -l" outfile
```
Should behave like:
```
$> < infile ls -l | wc -l > outfile
```
### Example 2:
```
$> ./pipex infile "grep a1" "wc -w" outfile
```
Should behave like:
```
$> < infile grep a1 | wc -w > outfile
```

## Features

**Command Chaining**: Chain two commands using a pipe.  
**File Redirection**: Redirect input from one file and output to another.  
**Error Handling**: Comprehensive error handling for common issues like incorrect commands and file permissions.  

## Installation

To build the project, clone the repository and run make:
```
git clone https://github.com/btoksoez/pipex.git
cd pipex
make
```

## Usage

Run the program with the following syntax:

```
./pipex file1 cmd1 cmd2 file2
```
file1: The input file.  
cmd1: The first command to be executed.  
cmd2: The second command to be executed.  
file2: The output file.  

### Example:

```
./pipex infile "ls -l" "grep pipex" outfile
```
This command takes infile as input, processes it with ls -l, pipes the output to grep pipex, and writes the final output to outfile.

## Explanation

**What is a Pipe?**  
A pipe is a mechanism for inter-process communication. It allows data to be passed from one process to another sequentially. In UNIX, a pipe is represented by the | character.

**What is a Fork?** 
In C, fork is a system call used to create a new process. The new process created by fork is called the child process. The child process runs concurrently with the parent process and has its own unique process ID.
