# 5.5. Built-in Functions
Python comes shipped with some predefined useful functions that we can use throughout our
code. We've already seen some built-in functions like `print()`, `input()` and `range()`.
This section some of the other useful ones.

??? example "`abs()`"

    Returns the [absolute value](https://en.wikipedia.org/wiki/Absolute_value) of a number.

    In a nutshell, this converts a negative value to positive. For example, `abs(-2.5)`
    returns `2.5`.

??? example "`divmod()`"

    Returns the quotient and remainder of a division operation.

    === "Code"

        ```py
        q, r = divmod(5, 2)
        print(q)
        print(r)
        ```

    === "Output"

        ```
        2.5
        1
        ```

??? example "`round()`"

    Rounds a number.

    For example, `round(5.2)` returns 5 and `round(5.6)` returns 6.

    This also takes a second parameter representing the decimals to
    round to. For example, `round(5.2793, 2)` returns `5.23`.

??? example "`len()`"

    Returns the length of a string or a sequence.

    For example, `len('hello john')` returns 10.

??? example "`ascii()`"

    Returns the ASCII code for a character.

    For example, `ascii('B')` returns 66.

??? example "`chr()`"

    Returns the character that maps to given ASCII code.

    For example, `chr(66)` returns `'B'`.

There are many other builtin functions that can be used in many tasks but all
of them cannot be listed here. See [Python documentation](https://docs.python.org/3/library/functions.html) for all functions.
