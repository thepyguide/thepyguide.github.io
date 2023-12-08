# 3.3. Indentation & Code blocks
Before we move on to learning more about conditionals, it is important that you know
about how indentation works in Python as indentation will be used a lot in Python.

## Indentation and Code block
Python is one of the many programming languages that use indentation for representing code
blocks. Other programmings like C, C++, JavaScript etc. use curly brackets to represent
code blocks.

Simply speaking, **Indentation are spaces in the beginning of line of code to represent that
a code is part of a code block.**

**A block of code comprises lines of code that are intended to execute under a certain
condition.** A colon `:` usually indicates the starting of a code block.

If we look at the following code similar to the code shown on previous page,

=== "Code"

    ```py
    age = int(input('Enter your age: '))

    if age >= 18:
        print('You are over 18.')
        print('You can drive.')
    else:
        print('You are under 18.')
        print('You cannot drive yet.')
    ```

=== "Output (Input: 23)"

    ```
    Enter your age: 23
    You are over 18.
    You can drive.
    ```

=== "Output (Input: 15)"

    ```
    Enter your age: 15
    You are under 18
    You cannot drive yet.
    ```

1. The colon indicates the starting of code block
2. The code block for the `if` statement
3. The code block for the `else` statement

In this code, both blocks of code comprise two lines of code only but could have any number
of lines.

An error will be raised if indentation is skipped:

=== "Code"

    ```py
    if age >= 18:
    print('You are over 18 so you can drive')
    ```

=== "Output"

    ```
      File "C:\XGuides\python\test.py", line 3
        print('You are over 18 so you can drive.')
        ^
    IndentationError: expected an indented block after 'if' statement on line 2
    ```

## Rules for Indentation

There are a following rules for indentation that are discussed below.

### Number of spaces
**It doesn't matter how many number of spaces are used for indentation but it should be at
least one.** The convention is to use 4 spaces (equivalent to a <kb>Tab</kb>).

In most code editors, pressing the Tab key would automatically indent by four spaces. Note
that four spaces are conventionally preferred over a raw Tab character and most code editors
treat pressing the Tab as equivalent to pressing spacebar four times.

=== "Code"

    ```py
    age = int(input('Enter your age: '))

    if age >= 18:
        print('You are over 18')  # 4 spaces
    else:
            print('You are not over 18')  # 8 spaces
    ```

=== "Output"

    ```
    Enter your age: 23
    You are over 18
    ```

Though no errors are raised by the code above, it is a good practice to keep the
indentation consistent throughout the code.

### Consistent indentation
The indentation in same code block must be consistent. That is, **in a certain code block
that has multiple lines, the indentation for each line should be same throughout that code
block.**

=== "Code"

    ```py linenums="1" hl_lines="7 8"
    age = int(input('Enter your age: '))

    if age >= 18:
        print('You are over 18')  # 4 spaces
        print('So you can drive')
    else:
            print('You are not over 18')  # 8 spaces
        print('So you cannot drive')  # 4 spaces
    ```

=== "Output"

    ```
      File "C:\XGuides\python\test.py", line 8
        print('So you cannot drive')  # 4 spaces
                                            ^
    IndentationError: unindent does not match any outer indentation level
    ```

As you can see, in the `else` code block, the first line is indented with 8 spaces
and the second line is indented with 4 spaces.

To resolve the error, either the second line in code block has to be indented 8 spaces
too or the first line has to be indented with 4 spaces.

!!! tip

    Writing pretty code is as important as writing efficient code. The conventional
    practice is to stick to 4 spaces for indentation throughout your code.

    While Python allows different indentation for individual code blocks, the best
    practice is to stay consistent.
