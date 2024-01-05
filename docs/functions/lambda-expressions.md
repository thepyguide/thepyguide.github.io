# 5.6. Lambda Expressions
Lambda expressions are small anonymous functions that can be defined in a single line. They
are called anonymous because they don't have a name on their own.

## Syntax
Anonymous functions are defined using the `lambda` keyword followed by list of parameters (if 
any) and the expression inside the function.

=== "Code"

    ```py
    adder = lambda a, b: a + b
    print(adder(5, 2))
    ```

=== "Output"

    ```
    7
    ```

Here, `adder` is an anonymous function that adds two integers. If we look at the syntax:

- The arguments function takes are defined before colon `:` and after `lambda` keyword
- The expression that the function returns is written after colon `:`

Lambda can only contain one expression after the `:` but supports all features of parameters
shown in [section 5.2. Arguments](./arguments.md) including default value, variadic arguments
and positional/keyword-only arguments.

## Application
Lambda functions are generally used when there is a need of a small function temporarily in
some code.

Another use of these functions are in closures that are defined using [nested functions](./return-value.md#returning-nested-functions).

For example:

=== "Code"

    ```py
    def factor(a):
        return lambda b: b * a

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
