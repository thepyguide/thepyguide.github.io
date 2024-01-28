# 3.4. Conditionals (Continued)
In [section 3.2. Basic Conditionals](./conditionals.md), we learned about some basic
constructs which are used to make decisions on the basis of some condition, more
specifically, the `if` and `else` constructs.

In this section, we'll dig deeper into these two statements and learn a new construct, `elif`.

## Nested `if` statements
You can write if statements inside if statements.

=== "Code"

    ```py linenums="1"
    age = int(input('Enter your age: '))
    test_score = float(input('Enter driving test score: '))

    if age >= 18:
        if test_score > 7:
            print('You are over 18 and passed driving test so you can drive.')
        else:
            print('You failed driving test so you cannot drive.')
    else:
        print('You cannot drive because you are under 18.')
    ```

=== "Output (age: 18, score: 10)"

    ```
    Enter your age: 18
    Enter driving test score: 10
    You are over 18 and passed driving test so you can drive.
    ```

=== "Output (age: 18, score: 3)"

    ```
    Enter your age: 18
    Enter driving test score: 3
    You failed driving test so you cannot drive.
    ```

=== "Output (age: 15, score: 10)"

    ```
    Enter your age: 15
    Enter driving test score: 10
    You cannot drive because you are under 18.
    ```

Note that each if statement has its own code block and is indented accordingly. The second if
statement is part of code block of first if statement.

!!! note "Using `and` instead of nested `if`"

    Nesting if statements is equivalent to using `and` on the two logical expressions. The
    above code can be shortened to following:

    === "Code"

        ```py linenums="1"
        age = int(input('Enter your age: '))
        test_score = float(input('Enter driving test score: '))

        if age >= 18 and test_score > 7:
            print('You are over 18 and passed driving test so you can drive.')
        else:
            print('You cannot drive.')
        ```

    === "Output (age: 18, score: 10)"

        ```
        Enter your age: 18
        Enter driving test score: 10
        You are over 18 and passed driving test so you can drive.
        ```

    === "Output (age: 18, score: 3)"

        ```
        Enter your age: 18
        Enter driving test score: 3
        You cannot drive.
        ```

    === "Output (age: 15, score: 10)"

        ```
        Enter your age: 15
        Enter driving test score: 10
        You cannot drive.
        ```

## The `elif` statement
The code shown below takes three numbers and outputs the largest number from the
three given numbers.

=== "Code"

    ```py
    a = int(input('Enter first number: '))
    b = int(input('Enter second number: '))
    c = int(input('Enter third number: '))

    if a >= b and a >= c:
        print(a, 'is largest number from given numbers')
    else:
        if b >= a and b >= c:
            print(b, 'is largest number from given numbers')
        else:
            if c >= a and c >= b:
                print(c, 'is largest number from given numbers')
    ```

=== "Output"

    ```
    Enter first number: 20
    Enter second number: 14
    Enter third number: 24
    24 is largest number from given numbers
    ```

The code works as expected. However, if you look at the lines below the first `else` statement,
there are so many nested if statements that it makes the code unnecessarily confusing.

To overcome this problem, we'll use the `elif` construct.

=== "Code"

    ```py
    a = int(input('Enter first number: '))
    b = int(input('Enter second number: '))
    c = int(input('Enter third number: '))

    if a >= b and a >= c:
        print(a, 'is largest number from given numbers')
    elif b >= a and b >= c:
        print(b, 'is largest number from given numbers')
    elif c >= a and c >= b:
        print(c, 'is largest number from given numbers')
    ```

=== "Output"

    ```
    Enter first number: 20
    Enter second number: 14
    Enter third number: 24
    24 is largest number from given numbers
    ```

As you can see, the code looks much easier to read now.

`elif` is short for "else if" and is equivalent to a nested if inside an else block:

=== "Without elif"

    ```py
    if condition_1:
        print('do something')
    else:
        if condition_2:
            print('do something else')
    ```

=== "With elif"

    ```py
    if condition_1:
        print('do something')
    elif condition_2:
        print('do something else')
    ```

`elif` is a way of saying "if previous condition didn't satisfy, check this condition"

You can stack as many `elif` statements as you want but note that first statement
is always an `if`.

=== "Code"

    ```py
    color = input('Enter a color: ')
    color = color.lower()  # (1)!

    if color == 'red':
        print('Color code for red: #FF0000')
    elif color == 'blue':
        print('Color code for blue: #0000FF')
    elif color == 'green':
        print('Color code for green: #008000')
    else:
        print(color, 'color is not supported')
    ```


    1. `color.lower()` is a method that converts the string to lowercase. This is done to make
        the comparison easier as user might give input in mixed case (e.g. `rEd` or `Red`).

        If we don't do this, then comparison would fail if user provides a mixed case input.
        (e.g. `"Red" == "red"` evaluates to False)

        **These methods are covered in detail in
        a [later section](../string-operations/string-methods.md).**

=== "Output (Red)"

    ```
    Enter a color: Red
    Color code for red is #FF0000
    ```

=== "Output (Green)"

    ```
    Enter a color: Green
    Color code for green is #008000
    ```

=== "Output (Magenta)"

    ```
    Enter a color: Magenta
    magenta color is not supported
    ```

The final `else` is executed when none of the conditions above it are satisfied.

---

## Exercise

!!! question "Exercise"

    === "Problem"

        Write a program that takes two numbers and calculate their sum.

        - if both numbers are even, add them
        - if both numbers are odd, subtract larger number with smaller
        - if one number is odd and other is even, multiply them

        Output the result of operation.

        **HINT:**

        If a number is even, the remainder of dividing it with 2 is always 0 otherwise
        it is 1. See [section 2.4. Mathematical Operations: Other Operations](../fundamentals/mathematical-operations.md#other-operations) for more information.

    === "Solution"

        ```py linenums="1"
        n1 = int(input('Enter first number: '))
        n2 = int(input('Enter second number: '))

        if (n1 % 2 == 0) and (n2 % 2 == 0):
            # both numbers are even
            result = n1 + n2
        elif (n1 % 2 == 1) and (n2 % 2 == 1):
            # both numbers are odd
            if n1 > n2:
                result = n1 - n2
            else:
                result = n2 - n1
        else:
            result = n1 * n2

        print(result)
        ```

        **Alternative approaches:**

        - Line 9-12 could be replaced with `result = abs(n2 - n1)` which returns the
          absolute (unsigned) value of subtraction result.
