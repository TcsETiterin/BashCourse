Certainly! Bash provides conditional statements such as `if`, `else`, `elif`, and `case` which allow you to create more complex and interactive scripts. Here's how you can use these constructs:

### `if`, `else`, and `elif`

#### Syntax

```bash
if [ condition ]; then
    # commands to execute if condition is true
elif [ another_condition ]; then
    # commands to execute if another_condition is true
else
    # commands to execute if none of the above conditions are true
fi
```

#### Example

```bash
#!/bin/bash

# Read a number from the user
echo "Enter a number:"
read number

if [ $number -gt 100 ]; then
    echo "The number is greater than 100."
elif [ $number -eq 100 ]; then
    echo "The number is exactly 100."
else
    echo "The number is less than 100."
fi
```

#### Key Points

- **Conditions**: Conditions are written within square brackets `[ ]`. You can use comparison operators like `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-le` (less than or equal), `-gt` (greater than), and `-ge` (greater than or equal).
- **Logical Operators**: You can use logical operators such as `-a` (and), `-o` (or), and `!` (not) to combine multiple conditions.

### `case` Statement

The `case` statement is used to simplify complex `if-elif-else` chains when comparing a variable against multiple values.

#### Syntax

```bash
case $variable in
    pattern1)
        # commands to execute if variable matches pattern1
        ;;
    pattern2)
        # commands to execute if variable matches pattern2
        ;;
    *)
        # commands to execute if variable matches none of the above patterns
        ;;
esac
```

#### Example

```bash
#!/bin/bash

# Read a fruit name from the user
echo "Enter a fruit (apple, banana, cherry):"
read fruit

case $fruit in
    apple)
        echo "You entered apple."
        ;;
    banana)
        echo "You entered banana."
        ;;
    cherry)
        echo "You entered cherry."
        ;;
    *)
        echo "Unknown fruit."
        ;;
esac
```

### Practical Combined Example

Here isCertainly! Bash provides conditional statements such as `if`, `else`, `elif`, and `case` which allow you to create more complex and interactive scripts. Here's a detailed explanation and examples on how you can use these constructs:

### `if`, `else`, and `elif`

#### Syntax

```bash
if [ condition ]; then
    # commands to execute if condition is true
elif [ another_condition ]; then
    # commands to execute if another_condition is true
else
    # commands to execute if none of the above conditions are true
fi
```

#### Example

```bash
#!/bin/bash

# Read a number from the user
echo "Enter a number:"
read number

if [ $number -gt 100 ]; then
    echo "The number is greater than 100."
elif [ $number -eq 100 ]; then
    echo "The number is exactly 100."
else
    echo "The number is less than 100."
fi
```

#### Key Points

- **Conditions**: Conditions are written within square brackets `[ ]`. You can use comparison operators like `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-le` (less than or equal), `-gt` (greater than), and `-ge` (greater than or equal).
- **Logical Operators**: You can use logical operators such as `&&` (and), `||` (or), and `!` (not) to combine multiple conditions.

### `case` Statement

The `case` statement is used to simplify complex `if-elif-else` chains when comparing a variable against multiple values.

#### Syntax

```bash
case $variable in
    pattern1)
        # commands to execute if variable matches pattern1
        ;;
    pattern2)
        # commands to execute if variable matches pattern2
        ;;
    *)
        # commands to execute if variable matches none of the above patterns
        ;;
esac
```

#### Example

```bash
#!/bin/bash

# Read a fruit name from the user
echo "Enter a fruit (apple, banana, cherry):"
read fruit

case $fruit in
    apple)
        echo "You entered apple."
        ;;
    banana)
        echo "You entered banana."
        ;;
    cherry)
        echo "You entered cherry."
        ;;
    *)
        echo "Unknown fruit."
        ;;
esac
```

### Practical Combined ExampleSure, here's a more detailed explanation with practical examples of using `if`, `else`, `elif`, and `case` statements in Bash:

### `if`, `else`, and `elif`

#### Syntax

```bash
if [ condition ]; then
    # commands to execute if condition is true
elif [ another_condition ]; then
    # commands to execute if another_condition is true
else
    # commands to execute if none of the above conditions are true
fi
```

#### Example

```bash
#!/bin/bash

# Read a number from the user
echo "Enter a number:"
read number

if [ $number -gt 100 ]; then
    echo "The number is greater than 100."
elif [ $number -eq 100 ]; then
    echo "The number is exactly 100."
else
    echo "The number is less than 100."
fi
```

#### Key Points

- **Conditions**: Conditions are written within square brackets `[ ]` or using the `[[ ]]` syntax which offers more functionality.
- **Comparison Operators**:
  - Numeric: `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-le` (less than or equal), `-gt` (greater than), and `-ge` (greater than or equal).
  - String: `==` (equal), `!=` (not equal), `<` (less than), `>` (greater than), `-n` (non-zero length), `-z` (zero length).
- **Logical Operators**: `&&` (and), `||` (or), and `!` (not) can be used to combine conditions.

### `case` Statement

The `case` statement simplifies checking a variable against multiple values, acting as a more readable alternative to complex `if-elif-else` chains.

#### Syntax

```bash
case $variable in
    pattern1)
        # commands to execute if variable matches pattern1
        ;;
    pattern2)
        # commands to execute if variable matches pattern2
        ;;
    *)
        # commands to execute if variable matches none of the above patterns
        ;;
esac
```

#### Example

```bash
#!/bin/bash

# Read a fruit name from the user
echo "Enter a fruit (apple, banana, cherry):"
read fruit

case $fruit in
    apple)
        echo "You entered apple            ;;
    banana)
        echo "You entered banana."
        ;;
    cherry)
        echo "You entered cherry."
        ;;
    *)
        echo "Unknown fruit."
        ;;
esac
```

### Practical Combined Example

Here’s a more complex example that combines `if`, `elif`, `else`, and `case` statements for a more complete script:

```bash
#!/bin/bash

echo "Welcome to the multi-functional script!"

# Read a number from the user
echo "Enter a number:"
read number

if [[ $number =~ ^[0-9]+$ ]]; then
    if [ $number -gt 100 ]; then
        echo "The number is greater than 100."

        echo "Enter a fruit (apple, banana, cherry, or any other):"
        read fruit

        case $fruit in
            apple)
                echo "You entered apple, and your number is greater than 100."
                ;;
            banana)
                echo "You entered banana, and your number is greater than 100."
                ;;
            cherry)
                echo "You entered cherry, and your number is greater than 100."
                ;;
            *)
                echo "You entered an unknown fruit, and your number is greater than 100."
                ;;
        esac

    elif [ $number -eq 100 ]; then
        echo "The number is exactly 100."
    else
        echo "The number is less than 100."
    fi
else
    echo "Please enter a valid number."
fi
```

### Key Points to Note:

- **Read User Input**: Use the `read` command to get input from the user.
- **Regex Checking**: `[[ $number =~ ^[0-9]+$ ]]` is used to check if the input is a valid number.
- **Nested Conditionals**: This script uses nested `if` and `case` statements to check multiple conditions in a compact manner.

These examples should help you get a good understanding of how to use conditional statements (`if`, `elif`, `else`, and `case`) in Bash scripts to make smarter and more interactive scripts.
