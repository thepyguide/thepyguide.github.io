# 5.1. Basics of Functions
Functions are named [codeblocks](../control-structures/indentation.md) that are only executed
when called and perform a specific task.

## Syntax
Functions are defined using the `def` keyword followed by name of function and any
arguments or parameters the function takes. The body of function is indented inside `def`.

For example, the following function calculates and returns the sum of two numbers:
```py
def add(n1, n2):
    return n1 + n2
```

Inspecting above code:

- `add` is the name of function.
- `n1` and `n2` are known as parameters or arguments.

## Calling a function
If you define a function in your program and simply run the program, you won't get any
output. This is because functions have to be called in order to be used.

=== "Code"

    ```py linenums="1"
    def add(n1, n2):
        return n1 + n2

    result = add(5, 2)
    print(result)
    ```

=== "Output"

    ```
    7
    ```

Here,

- The function is called on line 4.
- While calling, the value of `n1` parameter is set to `5` and `n2` set is to `2`.
- The function's body is executed and the value `7` is returned (as a result of line 2)
  which is then assigned to `result` variable.

## Arguments
A function can take one or more parameters or arguments. An argument is essentially an input
to a function that it uses while processing to generate the output.

=== "Code"

    ```py
    def greet():
        print('From greet() function:')
        print('Hello, World!')

    def greet_with_name(name):
        print('From greet_with_name() function:')
        print(f'Hello, {name}!')

    greet()
    greet_with_name('John')
    ```

=== "Output"

    ```
    From greet() function:
    Hello, World!
    From greet_with_name() function:
    Hello, John!
    ```

In above code, there are two functions. `greet` function does not take any arguments while
`greet_with_name` takes one argument: `name`.

More on arguments is covered in [section 5.2. Arguments](./arguments.md).

## Application
Here is an example of a comparatively complex function that calculates the factorial of a number:

=== "Code"

    ```py linenums="1"
    def factorial(n):
        fact = 1

        for i in range(1, n + 1):
            fact = n * i

        return fact

    print(factorial(3))
    print(factorial(5))
    print(factorial(6))
    ```

=== "Output"

    ```
    6
    120
    720
    ```

!!! note

    Factorial of a number is the product of that number with the numbers below it down
    to 1. For example, the factorial of 3 is `3 * 2 * 1` and factorial of 5 is
    `5 * 4 * 3 * 2 * 1`.

    Note that factorial of 1 and 0 is 1, and negative and fractional numbers don't have
    any factorial.

In this code, line 1-7 are defining the function and line 9-11 are calling the function three
times.

Note how the function is reused by calling it multiple times which is an application of
function. We don't have to rewrite the factorial logic again when using it, we simply
define the logic once as a function and call it whenever we want using the function name.

Another benefit of functions apart from reusability is organizing a large program in smaller
functions with each function performing a specific task. This way, it is easier to read, test
and debug.
