# 5.3. Return Value
Functions could return a value as a result of its calling. This page covers
various features and details about the `return` statement.

We've already seen in previous sections how return works. It returns a value
back to the caller.

=== "Code"

    ```py
    def add(n1, n2):
        return n1 + n2

    result = add(5, 2)
    print(result)
    ```

=== "Output"

    ```
    7
    ```

Here, `result` is assigned the value returned by function.

## Behaviour of `return`
The `return` statement is like a terminating statement for a function. When
you return something, the function terminates with the returned value.

=== "Code"

    ```py linenums="1"
    def check_password(password):
        if password == '1234':
            return True

        return False

    print(check_password('1234'))
    print(check_password('123456'))
    ```

=== "Output"

    ```
    True
    False
    ```

In this case, when we passed `1234` to `password` parameter, the if condition was
satisfied and `return True` on line 3 was executed. As soon as this happened, the
rest of the function body was skipped and `True` was yielded back to caller.

On the otherhand, when if condition wasn't satisfied (second function call), the
rest of function body was executed and `False` was returned.

This is equivalent to the following code but the `else` block is unnecessary here:

=== "Code"

    ```py
    # equivalent to code shown above
    def check_password(password):
        if password == '1234':
            return True
        else:
            # This else block is redundant and unnecessary!
            return False

    print(check_password('1234'))
    print(check_password('123456'))
    ```

=== "Output"

    ```
    True
    False
    ```

## Return nothing
In some cases, a function performs an action and returns nothing. "Nothing" in
Python is represented using the `None` value.

=== "Code"

    ```py
    def greet(name):
        print(f'Hello, {name}!')

    result = greet('John')
    print(result)
    ```

=== "Output"

    ```
    Hello, John!
    None
    ```

Since `greet()` has no `return` statement and isn't returning anything, it simply returns
a `None` value representing nothing was returned.

## Return vs Print
Do not confuse "returning a value" and "printing a value". In cases shown previously, both
might seem to do the same thing but there's a difference.

`print()` itself is a builtin function that simply outputs the given message to console.

`return` on the other hand, is a keyword used in a function to yield the value back to caller.

When we do, `print(2)`, we're telling Python to show the output on screen. In case of
`return 2` inside a function, we're telling Python to assign the value `2` to the call
of the given function.

=== "Code"

    ```py
    def print_value():
        print(12)

    def return_value():
        return 12

    print_value()  # prints 12
    return_value()  # does nothing
    ```

=== "Output"

    ```
    12
    ```

However, to print result of `return_value`, we use the print again:

=== "Code"

    ```py
    print_value()  # prints 12
    print(return_value())  # prints returned value of return_value()
    ```

=== "Output"

    ```
    12
    12
    ```

## Returning multiple values
A function could return a sequence of values. To do so, separate the values
to return using a comma `,`.

For example, consider this function that returns result of division and remainder:

=== "Code"

    ```py
    def divide_and_remainder(n1, n2):
        return n1 / n2, n1 % n2

    values = divide_and_remainder(5, 2)
    print(values[0])
    print(values[1])
    ```

=== "Output"

    ```
    2.5
    1
    ```

In fact, the values returned are stored as a [tuple](../data-structures/tuples/introduction.md)and could be
[unpacked](../data-structures/tuples/unpacking-tuples.md) too:

=== "Code"

    ```py
    quotient, remainder = divide_and_remainder(5, 2)
    print(quotient)
    print(remainder)
    ```

=== "Output"

    ```
    2.5
    1
    ```

!!! note

    Function shown in above example is same as builtin `divmod()` function.

## Returning Nested Functions
Nested functions are also referred to as closures and are used to retain values
from original (outer) function even after the original function is done executing.

=== "Code"

    ```py
    def factor(a):
        def inner(b):
            return a * b

        return inner

    doubler = factor(2)
    tripler = factor(3)

    print(doubler(20))
    print(tripler(20))
    ```

=== "Output"

    ```
    40
    60
    ```

In this case, we're creating a function inside `factor` everytime it is called and
returning it.
