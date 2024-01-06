# 6.1. `try` & `except` statements

<!--

TODO Comment:

For this section, the following sections are yet to be written:

- Raising Errors (raise statement)
- Custom Exceptions

Due to both of these topics being related to Object Oriented Programming
in some way or another, they cannot be added yet due to chronological
order of the guide.

These sections should be added at appropriate place after "Object Oriented
Programming" is added.

-->

When working with complex programs, you often encounter errors or exceptions.
In this section, we'll see how to handle these errors.

## Error vs Exception
In some other programming languages, errors and exceptions are two different 
things. In Python, both these terms generally mean the same thing but there
is still some difference.

**Errors** are issues that prevent a program from execution and cannot
be handled. For example, a `SyntaxError` cannot be handled and is
hence considered an "error".

**Exceptions** are issues that interrupt the flow of program and can
be handled. For example, `ZeroDivisionError` is an exception that
occurs when division by 0 is attempted. This can be handled and is
thus called an "exception".

Note that, at least in Python's context, **these two terms are generally
used synonymously and often mean the same thing**.

## Tracebacks
When we encounter an exception, we see a long error message that we
refer to as "traceback". See [section 2.5. Dealing with Errors](../fundamentals/dealing-with-errors.md) for more information.

=== "Code"

    ```py linenums="1" hl_lines="4"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    print(n1 / n2)  # (1)!
    ```

    1. This line is causing the exception.

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

This traceback holds useful information about the error including:

- the file in which error occured (line 5)
- the line where error occured (line 5)
- the description of error (line 7)
- and most importantly, the class of error (`ZeroDivisionError`) (line 7)

## `try`-`except`
We can handle these errors using the `try` and `except` statements.

=== "Code"

    ```py linenums="1" hl_lines="4 6"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    try:
        print(n1 / n2)
    except ZeroDivisionError:
        print('number 2 cannot be zero!')
    ```

=== "Output"

    ```
    Enter number 1: 8
    Enter number 2: 0
    number 2 cannot be zero!
    ```

Now our program does not crash with an exception. Instead, when that exception occurs, it is handled and an appropriate message is shown.

Let us look at the syntax now:

- The code indented under `try` block is code that could raise the
  error. It could be a single line or multiple lines.

- Line 6 uses the `except` statement followed by the class of error
  that should be handled, in this case, `ZeroDivisionError`.

    - `ZeroDivisionError` is one of many errors

- The code indented under the `except` block is code to execute when
  that error occurs.

## Multiple `except` statements
We can handle multiple exceptions by adding more `except` statements.

For example, `ValueError` is raised by `int` function when the
provided value cannot be converted to integer.

=== "Code"

    ```py
    x = 'hello'
    y = int(x)
    ```

=== "Error"

    ```
    Traceback (most recent call last):
      File "G:\thepyguide\main.py", line 2, in <module>
          y = int(x)
              ^^^^^^
    ValueError: invalid literal for int() with base 10: 'hello'
    ```

To avoid this, we can handle the `ValueError` alongside `ZeroDivisionError`.

=== "Code"

    ```py linenums="1" hl_lines="5 7"
    try:
        n1 = int(input('Enter number 1: '))
        n2 = int(input('Enter number 2: '))
        print(n1 / n2)
    except ZeroDivisionError:
        print('number 2 cannot be zero!')
    except ValueError:
        print('please provide a valid integer.')
    ```

=== "Output"

    ```
    Enter number 1: abc
    please provide a valid integer.
    ```

Note that it is considered a better practice to handle these errors
separately and keep the code in the `try` block minimal. Following
is an alternative but equivalent approach:

=== "Code"

    ```py
    try:
        n1 = int(input('Enter number 1: '))
        n2 = int(input('Enter number 2: '))
    except ValueError:
        print('please provide a valid integer.')

    try:
        print(n1 / n2)
    except ZeroDivisionError:
        print('number 2 cannot be zero!')
    ```

=== "Output"

    ```
    Enter number 1: abc
    please provide a valid integer.
    ```

## Single `except`, many exceptions
A single `except` can be used to handle multiple exceptions. This
is done by separating the exceptions to handle using a comma `,`.

=== "Code"

    ```py linenums="1" hl_lines="5 7"
    try:
        n1 = int(input('Enter number 1: '))
        n2 = int(input('Enter number 2: '))
        print(n1 / n2)
    except (ZeroDivisionError, ValueError):
        print('error occured!')
    ```

=== "Output #1"

    ```
    Enter number 1: abc
    error occured!
    ```

=== "Output #2"

    ```
    Enter number 1: 8
    Enter number 2: 0
    error occured!
    ```

However you'll notice that for both zero division, and conversion to integer
error, we're getting the same error message. We can deal with this using
the `as` keyword which is discussed in next heading.

## `as` keyword
Sometimes the error raised holds some useful information which we want to 
access. To do this, we have to store the error in a variable.

This is when `as` comes in handy. The `as` keyword is used to assign the raised error to a variable.

When we're using single except to handle multiple errors, we can use
`as` and builtin `isinstance` function to differentiate between the
handled errors.

=== "Code"

    ```py linenums="1"
    try:
        n1 = int(input('Enter number 1: '))
        n2 = int(input('Enter number 2: '))
        print(n1 / n2)
    except (ZeroDivisionError, ValueError) as error:
        if isinstance(error, ZeroDivisionError):
            print('number 2 cannot be zero!')
        elif isinstance(error, ValueError):
            print('conversion to integer is not possible')
    ```

=== "Output #1"

    ```
    Enter number 1: abc
    conversion to integer is not possible
    ```

=== "Output #2"

    ```
    Enter number 1: 8
    Enter number 2: 0
    number 2 cannot be zero!
    ```

!!! note

    `isinstance()` is a builtin function used for checking if something
    is an instance of a type. In this case, `ZeroDivisionError` and
    `ValueError` are two types and we're checking if `error` is an
    instance of those types.

Here, `error` is an instance of the handled error, either `ZeroDivisionError`
or `ValueError`.

## Bare except statements
Until this point, we used explicit `except` statements in which we provided
the list of exceptions that are to be handled.

There are also "bare" except statements in which exceptions to be
handled are not provided and it catches any exception raised.

```py
n1 = int(input('Enter number 1: '))
n2 = int(input('Enter number 2: '))

try:
    print(n1 / n2)
except:
    print('number 2 cannot be zero!')
```

In this code, the `except` is bare as it does not provide any exceptions
that must be handled. This except would catch any error, not necessarily
`ZeroDivisionError`, that occurs in try block.

### Drawback
**Bare `except` statements are considered a bad practice.** This is
because bare except handles all kind of errors, even those that are
not meant to be handled.

Consider the following code:
```py
while True:
    print('Hello')
```

When you run this program, it continously prints the message in console
in an endless loop. If you want to terminate the program, you can press
++ctrl+c++ which raises a `KeyboardInterrupt` exception and terminates
the program.

If we put this code into a `try`-`except` block with bare except block. The
`KeyboardInterrupt` exception is handled by `except` and program doesn't
terminate as desired.

```py
try:
    while True:
        print('Hello')
except:  # the wrong way
    print('you cannot exit the program')
```

This is why, due to handling of unexpected and unwanted errors, bare
excepts are not used in good code.

### Alternative
An alternative to bare except is handling `Exception` exception. This
exception is the base class for all "should be handled" exceptions.

Exceptions like `KeyboardInterrupt` and `SystemExit` that should not
be handled are not included in this class so they are not handled.

```py
try:
    while True:
        print('Hello')
except Exception:  # the right way
    print('error occured but ignored')
```

Above except statement will catch all the appropriate exceptions.
