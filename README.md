# Minishell

A minimal version of Bash - A simple shell implementation written in C.

## 📋 About The Project

Minishell is a project that mimics the basic functionality of Unix shells (especially Bash). This project teaches system programming concepts such as process management, pipes, redirections, and signal handling.

## 🎯 Features

### Core Features
- ✅ Display a prompt
- ✅ Command history
- ✅ Search and execute executables (using $PATH)
- ✅ Work with relative and absolute paths
- ✅ Environment variables
- ✅ Exit status ($?)

### Redirections
- `<` : Input redirection
- `>` : Output redirection
- `<<` : Heredoc
- `>>` : Append output redirection

### Pipes
- `|` : Pipe - passes output of one command to input of another
- Multiple pipes are supported

### Signal Handling
- `ctrl-C` : Display new prompt (SIGINT)
- `ctrl-D` : Exit shell (EOF)
- `ctrl-\` : Do nothing (SIGQUIT)

### Built-in Commands
- `echo` (with -n option)
- `cd` (with relative or absolute path)
- `pwd` (no options)
- `export` (no options)
- `unset` (no options)
- `env` (no options)
- `exit` (no options)

### Special Features
- Single quote (`'`) and double quote (`"`) handling
- Environment variable expansion (`$VAR`)
- Exit status (`$?`)

## 🛠️ Technologies Used

- **C Language** (97.6%)
- **Makefile** (2.4%)
- Readline library
- System calls (fork, execve, pipe, dup2, etc.)

## 📦 Installation

### Requirements

```bash
# Install readline library
# macOS
brew install readline

# Linux (Debian/Ubuntu)
sudo apt-get install libreadline-dev

# Linux (Fedora)
sudo dnf install readline-devel
```

### Compilation

```bash
make        # Compile the program
make clean  # Clean object files
make fclean # Clean all compilation outputs
make re     # Recompile
```

## 💻 Usage

```bash
./minishell
```

### Example Commands:

```bash
# Simple commands
minishell$ ls -la
minishell$ pwd
minishell$ echo "Hello World"

# Using pipes
minishell$ ls | grep minishell
minishell$ cat file.txt | grep "test" | wc -l

# Redirections
minishell$ echo "test" > output.txt
minishell$ cat < input.txt
minishell$ ls >> output.txt

# Heredoc
minishell$ cat << EOF
> line 1
> line 2
> EOF

# Environment variables
minishell$ echo $PATH
minishell$ echo $USER
minishell$ export MY_VAR="test"
minishell$ echo $MY_VAR

# Built-in commands
minishell$ cd /tmp
minishell$ pwd
minishell$ env
minishell$ exit

# Exit status
minishell$ ls
minishell$ echo $?
```

## 🧠 Architecture and Design

### 1. Lexer (Lexical Analysis)
- Splits input string into tokens
- Handles quoted strings
- Recognizes special characters (|, <, >, <<, >>)

### 2. Parser (Syntax Analysis)
- Converts tokens into command structures
- Detects syntax errors
- Creates pipe chains

### 3. Expander
- Expands environment variables
- Expands exit status ($?)
- Applies quote rules

### 4. Executor
- Executes built-in commands directly
- Uses fork/execve for external commands
- Handles pipes and redirections
- Manages signals

## 📚 Important System Calls

- `readline()` : Get input from user
- `fork()` : Create new process
- `execve()` : Execute program
- `pipe()` : Create pipe
- `dup2()` : Duplicate file descriptor
- `wait()/waitpid()` : Wait for child process
- `signal()` : Handle signals
- `access()` : Check file access permissions

## ⚠️ Important Notes

- No memory leaks (except readline)
- Signal handling must work correctly
- Should behave like Bash
- Must show error messages for invalid syntax
- Global variable can only be used for signals

## 🔍 42 Norm

This project complies with 42 school's **Norm** standards:
- Maximum 25 lines per function
- Maximum 80 characters per line
- Maximum 4 parameters per function

## 📝 Test Cases

```bash
# Simple commands
ls
ls -la
/bin/ls

# Pipes
ls | cat
cat file.txt | grep test | wc -l

# Redirections
echo test > file
cat < file
ls >> file
cat << EOF

# Environment variables
echo $PATH
echo $USER
export TEST=123
echo $TEST

# Exit status
ls
echo $?
ls /invalid/path
echo $?

# Built-ins
cd ..
pwd
env
exit

# Quotes
echo "$USER"
echo '$USER'
echo "test 'test' test"

# Signals
ctrl-C
ctrl-D
ctrl-\
```

## 👤 Developer

**TroubledKezoo1**

Project Link: [https://github.com/TroubledKezoo1/Minishell](https://github.com/TroubledKezoo1/Minishell)

## 📖 Resources

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Writing Your Own Shell](https://www.cs.purdue.edu/homes/grr/SystemsProgrammingBook/Book/Chapter5-WritingYourOwnShell.pdf)
- [Unix Process Management](https://www.geeksforgeeks.org/process-management-in-linux/)

---

*42 School - Minishell Project*