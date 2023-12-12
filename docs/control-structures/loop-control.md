# 3.7. Loop Control
In this section, we'll learn about two statements that are used to control a loop's flow.

## `break` statement
The `break` statement is used to interrupt the loop and terminate it. This statement will
terminate the loop immediately regardless of whether the loop condition is True or not.

### Using a `while` loop

=== "Code"

    ```py
    while True:  # (1)!
        password = input('Enter password: ')

        if password == 'python':
            break

        print('Invalid Password')

    print('Access granted')
    ```

    1. `while True:` indicates a loop that runs forever or until `break` statement is not executed.

=== "Output"

    ``` hl_lines="1 3 5"
    Enter password: wrong
    Invalid Password
    Enter password: random input
    Invalid Password
    Enter password: python
    Access granted
    ```

    _(Highlighted lines are inputs)_

In above `while` loop example, the program will repeatedly prompt for password
until the correct one is not entered, in this case `python`.

### Using a `for` loop

=== "Code"

    ```py
    word = input('Enter a word')

    for char in word:
        if char == 'a':
            print('letter A found in word')
            break

        print(char)
    ```

=== "Output (`gun`)"

    ``` hl_lines="1"
    Enter a word: gun
    g
    u
    n
    ```

    _(Highlighted lines are inputs)_

=== "Output (`london`)"

    ``` hl_lines="1"
    Enter a word: london
    l
    o
    n
    d
    o
    n
    ```

    _(Highlighted lines are inputs)_

=== "Output (`practice`)"

    ``` hl_lines="1"
    Enter a word: practice
    p
    r
    letter A found in word
    ```

    _(Highlighted lines are inputs)_

In this example, the program takes a word as input and prints its characters. As soon as
an `a` character is found, the program outputs a message and loop terminates.

## `continue` statement
The `continue` statement is used to continue to next iteration without executing the
rest of loop body.

### Using a `while` loop

=== "Code"

    ```py
    x = 1

    while x <= 10:
        if x == 3:
            continue

        result = x * 2
        print('2', '*', x, '=', result)
        x = x + 1
    ```

=== "Output"

    ```
    2 * 1 = 2
    2 * 2 = 4
    2 * 4 = 8
    2 * 5 = 10
    2 * 6 = 12
    2 * 7 = 14
    2 * 8 = 16
    2 * 9 = 18
    2 * 10 = 20
    ```

Above program prints the times table for 2 however it doesn't print the multiple of 2 with 3.

### Using a `for` loop

The same program could be written with a `for` loop.

=== "Code"

    ```py
    for x in range(1, 11)
        if x == 3:
            continue

        result = x * 2
        print('2', '*', x, '=', result)
    ```

=== "Output"

    ```
    2 * 1 = 2
    2 * 2 = 4
    2 * 4 = 8
    2 * 5 = 10
    2 * 6 = 12
    2 * 7 = 14
    2 * 8 = 16
    2 * 9 = 18
    2 * 10 = 20
    ```
