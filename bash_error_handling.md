Error handling is an essential part of writing robust and reliable Bash scripts. Bash provides several mechanisms to detect and handle errors, giving you control over what happens when commands fail or unexpected conditions occur.

### Basic Error Handling

#### Exit Status
Every command in Bash returns an exit status when it finishes. The exit status is an integer where `0` typically indicates success, and any non-zero value indicates an error.

To check the exit status of the last executed command, you can use the special variable `$?`.

```bash
# Execute a command
mkdir /tmp/some_directory

# Check the exit status
if [ $? -eq 0 ]; then
    echo "Command succeeded."
else
    echo "Command failed."
fi
```

### `set` Built-in Command

The `set` built-in command can be used to change the behavior of the current script. Some useful options for error handling are:

- `-e` or `-o errexit`: Exit immediately if any command exits with a non-zero status.
- `-u` or `-o nounset`: Treat unset variables as an error and exit immediately.
- `-o pipefail`: Returns the exit status of the last command in the pipeline that failed.

You can enable these options as follows:

```bash
set -euo pipefail

mkdir /tmp/some_directory   # If this fails, the script will exit immediately
echo "This will not be printed if the previous command fails."
```

### `trap` Command

The `trap` command allows you to execute a command or a function when the script exits or receives a signal. This is useful for cleaning up resources or printing error messages.

#### Example: Cleaning Up Resources

```bash
# Create a temporary file
tmpfile=$(mktemp)

# Ensure the temporary file is deleted on script exit
trap 'rm -f "$tmpfile"' EXIT

# Rest of the script using the temporary file
echo "Hello, World!" > "$tmpfile"
```

#### Example: Custom Error Messages

```bash
set -euo pipefail

# Function to handle errors
error_handler() {
    echo "An error occurred. Exiting." >&2
}

# Call error_handler function on any error
trap error_handler ERR

# Commands that might fail
false  # This command will fail and trigger the error_handler
```

### Using Subshells

Subshells can be used to isolate commands. If a command fails within a subshellError handling is an essential part of writing robust and reliable Bash scripts. Bash provides several mechanisms to detect and handle errors, giving you control over what happens when commands fail or unexpected conditions occur.

### Basic Error Handling

#### Exit Status
Every command in Bash returns an exit status when it finishes. The exit status is an integer where `0` typically indicates success, and any non-zero value indicates an error.

To check the exit status of the last executed command, you can use the special variable `$?`.

```bash
# Execute a command
mkdir /tmp/some_directory

# Check the exit status
if [ $? -eq 0 ]; then
    echo "Command succeeded."
else
    echo "Command failed."
fi
```

### `set` Built-in Command

The `set` built-in command can be used to change the behavior of the current script. Some useful options for error handling are:

- `-e` or `-o errexit`: Exit immediately if any command exits with a non-zero status.
- `-u` or `-o nounset`: Treat unset variables as an error and exit immediately.
- `-o pipefail`: Returns the exit status of the last command in the pipeline that failed.

You can enable these options as follows:

```bash
set -euo pipefail

mkdir /tmp/some_directory   # If this fails, the script will exit immediately
echo "This will not be printed if the previous command fails."
```

### `trap` Command

The `trap` command allows you to execute a command or a function when the script exits or receives a signal. This is useful for cleaning up resources or printing error messages.

#### Example: Cleaning Up Resources

```bash
# Create a temporary file
tmpfile=$(mktemp)

# Ensure the temporary file is deleted on script exit
trap 'rm -f "$tmpfile"' EXIT

# Rest of the script using the temporary file
echo "Hello, World!" > "$tmpfile"
```

#### Example: Custom Error Messages

```bash
set -euo pipefail

# Function to handle errors
error_handler() {
    echo "An error occurred. Exiting." >&2
}

# Call error_handler function on any error
trap error_handler ERR

# Commands that might fail
false  # This command will fail and trigger the error_handler
```

### Using `||` for Conditional Execution

The `||` operator can be used to run a command or series ofcommands if the preceding command fails. This is useful for inline error handling and can be combined with commands like `echo` or custom error functions for simple error reporting.

#### `||` Example

```bash
mkdir /tmp/some_directory || { echo "Failed to create directory"; exit 1; }
```

In this example, if `mkdir` fails, the echo statement and the exit command are executed immediately.

### Using `&&` for Conditional Execution

Similarly, the `&&` operator can be used to run a command only if the preceding command succeeds.

#### `&&` Example

```bash
mkdir /tmp/some_directory && echo "Directory created successfully."
```

This example will only print the success message if the directory creation succeeds.

### Functions and Error Handling

Using functions can help modularize script logic and error handling. You can set up error handling within the function itself.

#### Example: Error-Handled Function

```bash
set -euo pipefail

# Error handler function
error_handler() {
    local err=$?
    echo "Error in ${BASH_SOURCE[1]} on line ${BASH_LINENO[0]}. Exiting with status $err." >&2
    exit $err
}

# Set trap for ERR within functions
trap error_handler ERR

# Function definition
create_directory() {
    local dir=$1
    mkdir "$dir" || { echo "Failed to create directory: $dir"; return 1; }
    echo "Directory $dir created successfully."
}

# Call the function
create_directory /tmp/some_directory
```

### Summary

Error handling in Bash can be managed using various techniques:

1. **Exit Status Checking**: Using `$?` to check the exit status of commands.
2. **`set` Command**: Enabling options like `-e`, `-u`, and `-o pipefail` to control script behavior.
3. **`trap` Command**: Using `trap` to execute cleanup or error-handling functions upon exit or errors.
4. **Conditional Execution**: Using `||` and `&&` for inline error handling.
5. **Functions**: Encapsulating error-prone code in functions with their own error handling.

By incorporating these techniques, you can make your Bash scripts more robust and easier to debug.
