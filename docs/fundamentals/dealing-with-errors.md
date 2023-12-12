# 2.5. Dealing with Errors
Sometimes your code doesn't behave the way it should. This section will guide you
through the process of dealing with errors so you know what to do when things go wrong.

## Introduction to Errors
An error occurs when your code does something which isn't allowed or isn't possible. Mainly
there are two types of errors:

- Syntax Error
- Runtime Error

**Syntax Error** occurs when you break the rules of a language grammar. Just like English
has grammar, programming languages have some rules too. If you break these rules, you get
a syntax error. In other words, this error occurs when you write something that computer
cannot understand.

Generally, syntax errors are easier to find. Due to this, the Python interpreter
can detect these errors at the start of program and can alert you before program
even executes.

An example of syntax error:

=== "Code"

    ```py
    print('Hello world)
    ```

    In this code snippet, we are missing a closing quotation.

=== "Output"

    ```
      File "G:\thepyguide\main.py", line 1
        print('Hello world)
              ^
    SyntaxError: unterminated string literal (detected at line 1)
    ```

**Runtime Error** relate more to unexpected behaviour at execution time. This error
isn't detected before execution. This is why we often refer to them with a popular
term: "bugs".

For example, if we have a program that takes user input and divides two numbers, a
runtime error can occur when user provides 0 for denominator:

=== "Code"

    ```py
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    print(n1 / n2)
    ```

=== "Output"

    ```
    Enter number 1: 8
    Enter number 2: 0
    Traceback (most recent call last):
      File "G:\thepyguide\main.py", line 4, in <module>
          print(n1 / n2)
                ~~~^~~~
    ZeroDivisionError: division by zero
    ```

## Understanding errors
We understand how much the word "error" sounds scary but if you can understand the
long error messages. You can tackle any error.

When an error occurs, Python generates an error message known as "error traceback". This
traceback message tells exactly where the error is coming from.

For example in above error, if you look closely, the error traceback tells us following
bits of useful information:

- The name and path of file in which error occured (test.py)
- The exact line where it occured (line 4)
- The error message describing what happened (division by zero)

=== "Error"

    ``` linenums="1" hl_lines="4 5 6 7"
    Enter number 1: 8
    Enter number 2: 0
    Traceback (most recent call last):
      File "G:\thepyguide\main.py", line 4, in <module>
          print(n1 / n2)
                ~~~^~~~
    ZeroDivisionError: division by zero
    ```

    - Line 4 tells us the file name and line number that caused the error.
    - Line 5 and 6 shows us the bit of code that caused the error.
    - Line 7 shows the name of error, `ZeroDivisionError`, and an error message
      describing the cause of error.

=== "Code"

    ```py linenums="1" hl_lines="4"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    print(n1 / n2)  # (1)!
    ```

    1. This is where the error occured.

!!! tip

    The rule of thumb is to always read the error messages. Sometimes the error
    message might not make sense to you; In that case, remember, Google is your friend.

