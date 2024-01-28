# 2.2. I/O Operations
In this section, we'll be looking at how we can take input from user and produce an output.

## Formatting output
For a recap, in the [1.3. Hello World](../getting-started/the-first-program.md), we learnt
about the `print()` function which allows us to output messages.

The `print()` function provides some extra functionality that allows us to format our output.

### Multiple messages
We can pass multiple messages to this function that will be separated by space
when outputing:

=== "Code"

    ```py
    print('Hello', 'World!')
    ```

=== "Output"

    ```
    Hello World!
    ```

This is particulary useful when outputting values of a variable:

=== "Code"

    ```py
    age = 20
    print('The age of this user is', age, 'years.')
    ```

=== "Output"

    ```
    The age of this user is 20 years.
    ```

By default, the passed messages are joined with space as a separator. If you want
to change the separator, we can do that by passing a `sep` parameter:

=== "Code"

    ```py
    print('apple', 'banana', 'peach', sep=', ')
    ```

=== "Output"

    ```
    apple, banana, peach
    ```

### Newlines and ending
In order to move to a newline when outputing messages, a special "escape character" is used. 
This escape character is ``\n``.

!!! info "Escape Characters"

    Other than new line escape characters, there are various other escape characters
    for various purposes which will be discussed later in this guide.

For example:

=== "Code"

    ```py
    print('Line 1\nLine2\nLine3')
    ```

=== "Output"

    ```
    Line 1
    Line 2
    Line 3
    ```

Note that when we call a print statement. The output message automatically appended with
a new line character. Hence, the following code produces the same output as above:

=== "Code"

    ```py
    print('Line 1')
    print('Line 2')
    print('Line 3')
    ```

=== "Output"

    ```
    Line 1
    Line 2
    Line 3
    ```

If we don't want the end of each output to be new line, we can pass another character
to `end` argument. By default, `end` is set to `\n`

=== "Code"

    ```py
    print('Line 1', end='.')
    print('Line 2', end='.')
    print('Line 3', end='.')
    ```

=== "Output"

    ```
    Line 1.Line 2.Line 3.
    ```


## Taking user input
A program is incomplete without user input. Every program requires an input in some
way or another.

The most basic way of taking user input is by using the `input()` function:

=== "Code"

    ```py
    name = input('Enter your name: ') # (1)!
    print('Hello,', name)
    ```

    1. If we don't pass any message to `input()` function, no prompt is shown
       in the terminal.

=== "Output"

    ```py
    Enter your name: John # (1)!
    Hello, John
    ```

    1. "John" is the given user input.

### Converting input type
The `input()` function returns the input as a string (`str` data type). In cases
where you are expecting a different type, you must convert the string to that type
explicitly.

For example, the following program takes two numbers and adds them:

=== "Code"

    ```py
    n1 = input('Enter number 1: ')
    n2 = input('Enter number 2: ')

    n1 = int(n1)  # (1)!
    n2 = int(n2)  # (2)!

    print(n1 + n2)
    ```

    1. n1 converted to `int` type.
    2. n2 converted to `int` type.

=== "Output"

    ```
    Enter number 1: 20
    Enter number 2: 50
    70
    ```

For more information on data type conversion, take a look at the
[2.1. Variables and Data Types: Converting data types](./variables-and-data-types.md#converting-data-types) topic.
