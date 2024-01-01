# 3.5. Truth Value
By definition, truth value of `X` is the True/False value returned when `bool(X)` is performed.

In general, if any value has some content, it has a truth value of `True`. If a value does
not have any content, its truth value is `False`.

## Truth value for `str` type
A string has a truth value of `True` when it is non-empty.

=== "Code"

    ```py
    print(bool(''))
    print(bool('a'))
    ```

=== "Output"

    ```
    False
    True
    ```

In first line, an empty string has truth value of False and in second line, a non-empty string
has truth value of True.

Note that a space is also considered a character so truth value of `" "` is also True.

=== "Code"

    ```py
    print(bool(' '))
    ```

=== "Output"

    ```
    True
    ```

Even if string has no actual characters, a "space" is still considered a character so string is
not empty and has truth value of True.

## Truth value for `int` type
An integer has a truth value of `True` when it is non-zero.

=== "Code"

    ```py
    print(bool(0))
    print(bool(1))
    print(bool(2))
    ```

=== "Output"

    ```
    False
    True
    True
    ```

## Truth value for `float` type
A floating point number has a truth value of `True` when it is non-zero.

=== "Code"

    ```py
    print(bool(0.0))
    print(bool(1.2))
    ```

=== "Output"

    ```
    False
    True
    ```

Note that the value has to be absolutely `0.0` to be False. A value as small as `0.00000001`
also has some content so its truth value is True.

=== "Code"

    ```py
    print(bool(0.0))
    print(bool(0.000000001))
    ```

=== "Output"

    ```
    False
    True
    ```

## Using truth values
Truth values are used in `if`/`elif` statements. They are a shorthand to checking if the
content of variable being checked is non-empty.

=== "Output"

    ```py
    content = ''

    if content:
        print('Non-empty')
    else:
        print('Empty')
    ```

=== "Code"

    ```
    Empty
    ```

Here, the `if` statement checks if the value of `content` is non-empty. This is roughly equivalent
to:

```py
content = ''

if content != '':
    print('Non-empty')
else:
    print('Empty')
```

Same goes for integers and floats. If an integer is non-zero, only then it would evaluate
to True in an if statement.
