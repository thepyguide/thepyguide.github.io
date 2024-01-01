# 3.1. Basic Conditionals
Every program needs to make some decisions during its executions. These decisions are typically
made on the basis of the user input. To make such decisions, we use conditional statements.

In this article, we'll understand the basic `if` and `else` statements used for
making decisions on the basis of logical expressions (conditions).

## `if` statement
Let us understand this with an example:

=== "Code"

    ```py
    age = int(input('Enter your age: '))

    if age >= 18:
        print('You are over 18.')
        print('You can drive.')
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
    ```

As you can see, when we give a number greater than or equal to 18, the program produces
an output showing that the user can drive.

`age > 18` is a [logical expression](./logical-operations.md) and when it evaluates to `True`,
the indented lines are executed. Logical expressions are covered in detail in a later topic.

## `else` statement
However, if the number is less than 18, the program simply exits without any message
which seems a little odd. To fix this, we can include an `else` block:

=== "Code"

    ```py linenums="1" hl_lines="7 8"
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
    You are under 18.
    You cannot drive yet.
    ```

The `else` block is executed when the `if` is not executed.

## Indentation
The lines after `if` statement are indented (leading spaces before the line of code) to
indicate that they are executed only when the `if` condition is satisfied.

```py linenums="1" hl_lines="4 5"
age = int(input('Enter your age: '))

if age >= 18:
    print('You are over 18.') # (1)!
    print('You can drive.')
else:
    print('You are under 18.')
    print('You cannot drive yet.')
```

1. Highlighted lines indicate the code block executed when expression `age >= 18` evaluates
to True.

Similarly, the lines after `else` statement are indented to indicate that they are executed only
when `else` is reached (i.e. when condition is not satisfied.)

```py linenums="1" hl_lines="7 8"
age = int(input('Enter your age: '))

if age >= 18:
    print('You are over 18.')
    print('You can drive.')
else:
    print('You are under 18.') # (1)!
    print('You cannot drive yet.')
```

1. Highlighted lines indicate the code block executed when expression `age >= 18` evaluates
to False.

---

In Python, the indentation (i.e. the leading spaces before the code) in both clause bodies
is significant. The next page discusses the concept of indentation in detail.

The concept of conditionals is continued in [3.4. Conditionals (Continued)](.conditionals-continued.md)
