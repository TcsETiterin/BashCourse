Bash provides several looping structures (`for`, `while`, and `until`) to perform repetitive tasks effectively. Here's an overview of each, along with practical examples.

### `for` Loop

The `for` loop iterates over a list of items, executing commands for each item.

#### Syntax

```bash
for variable in list; do
    # commands to execute
done
```

#### Example

```bash
#!/bin/bash

# Iterate over a list of numbers
for number in 1 2 3 4 5; do
    echo "Number: $number"
done

# Iterate over a list of files in a directory
for file in /path/to/directory/*; do
    echo "File: $file"
done
```

### `while` Loop

The `while` loop executes commands as long as a specified condition is true.

#### Syntax

```bash
while [ condition ]; do
    # commands to execute
done
```

#### Example

```bash
#!/bin/bash

# Initialize a counter
counter=1

# Execute the loop while the condition is true
while [ $counter -le 5 ]; do
    echo "Counter: $counter"
    ((counter++))  # Increment the counter
done
```

### `until` Loop

The `until` loop is similar to the `while` loop, but it executes commands until a specified condition becomes true (i.e., it continues while the condition is false).

#### Syntax

```bash
until [ condition ]; do
    # commands to execute
done
```

#### Example

```bash
#!/bin/bash

# Initialize a counter
counter=1

# Execute the loop until the condition is true
until [ $counter -gt 5 ]; do
    echo "Counter: $counter"
    ((counter++))  # Increment the counter
done
```

### Practical Combined Example

Here's a more complex example that combines different loop structures for a more complete script:

```bash
#!/bin/bash

# Using a for loop to iterate through a list of files and count lines in each file
echo "Counting lines in text files:"
for file in *.txt; do
    line_count=$(wc -l < "$file")
    echo "$file: $line_count lines"
done

# Using a while loop to read user input until a specified condition
correct_password="mypassword"
user_input=""

while [ "$user_input" !=
```bash
"$correct_password" ]; do
    read -sp "Enter the password: " user_input
    echo
    if [ "$user_input" != "$correct_password" ]; then
        echo "Incorrect password. Try again."
    fi
done

echo "Password accepted!"

# Using an until loop to wait for a specific file to appear in a directory
echo "Waiting for the 'trigger.txt' file to appear in the current directory..."
until [ -f "./trigger.txt" ]; do
    sleep 1  # Check every second
    echo "Checking..."
done

echo "'trigger.txt' has appeared!"
```

### Key Points to Note:

- **`for` Loop Variables**: The variable in the `for` loop can be any name, and it's assigned the value of each item in the list sequentially.
- **File Iteration**: Wildcards like `*.txt` can be used to iterate through files that match a specific pattern.
- **Conditional Expressions**: Both `while` and `until` loops use conditional expressions inside square brackets `[ ]`.
  - For numbers, use `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`.
  - For strings, use `==`, `!=`, `-n` (non-zero length), `-z` (zero length).
- **Incrementing Counters**: The `((counter++))` syntax is used to increment counters.
- **User Input**: The `read -sp` command reads input from the user without displaying it (useful for passwords).
- **File Existence Check**: The `-f` operator checks if a file exists.

These examples illustrate how you can use `for`, `while`, and `until` loops in Bash to automate repetitive tasks, handle user input, and perform file system checks. With these constructs, you can build more efficient and powerful Bash scripts.
