# 6.2. `else` & `finally` statements
Apart from `except`, we can also use `else` and a `finally` statement
with a `try` block. These are covered in this section.

## `try`-`except`-`else`
An `else` block can be added after `except` block which would be executed
when error does not occur.

=== "Code"

    ```py linenums="1" hl_lines="7"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    try:
        print(n1 / n2)
    except ZeroDivisionError:
        print('number 2 cannot be zero!')
    else:
        print('division successful')
    ```

=== "Output #1"

    ```
    Enter number 1: 8
    Enter number 2: 2
    4.0
    division successful
    ```

=== "Output #2"

    ``` 
    Enter number 1: 8
    Enter number 2: 0
    number 2 cannot be zero!
    ```

This `else` is not executed when error is raised and `except` is executed.

## `try`-`except`-`finally`
The `finally` block is used with `try` to execute the code after all the
error handling is performed:

=== "Code"

    ```py linenums="1" hl_lines="7"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    try:
        print(n1 / n2)
    except ZeroDivisionError:
        print('number 2 cannot be zero!')
    finally:
        print('program ended')
    ```

=== "Output #1"

    ```
    Enter number 1: 8
    Enter number 2: 2
    4.0
    program ended
    ```

=== "Output #2"

    ``` 
    Enter number 1: 8
    Enter number 2: 0
    number 2 cannot be zero!
    program ended
    ```

The `finally` block is always executed at the end once all other blocks
are done executing.

### `try-finally`
`try` can be paired with `finally` without an `except`. In this case,
the code in `try` block is executed and if an error occurs, `finally`
block is executed before raising the error.

=== "Code"

    ```py linenums="1" hl_lines="7"
    n1 = int(input('Enter number 1: '))
    n2 = int(input('Enter number 2: '))

    try:
        print(n1 / n2)
    finally:
        print('program ended')
    ```

=== "Output #1"

    ```
    Enter number 1: 8
    Enter number 2: 2
    4.0
    program ended
    ```

=== "Output #2"

    ``` 
    Enter number 1: 8
    Enter number 2: 0
    number 2 cannot be zero!
    program ended
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 5, in <module>
        print(n1 / n2)
              ~~~^~~~
    ZeroDivisionError: division by zero
    ```

### `try`-`except`-`else`-`finally`
`finally` can also be applied with `try`-`except`-`else`.

```py
try:
    # do something here
    ...
except Exception:
    # handle Exception here
    ...
else:
    # if no error occurs, do something here
    ...
finally:
    # regardless of error occurs or not, do this
    # at the end
    ...
```

!!! warning "Order of blocks"

    Following rules should must be followed for order of
    try, except, else and finally blocks:

    - The first block is always `try`.
    - `else` can only be added when `except` is used.
    - `else` is always put after all the `except` blocks.
    - `finally` is always the last block.

    In short, the only valid blocks order are:

    - `try`-`except`
    - `try`-`except`-`else`
    - `try`-`except`-`else`-`finally`
    - `try`-`except`-`finally`
    - `try`-`finally`

