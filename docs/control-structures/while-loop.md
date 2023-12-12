# 3.6. The "while" loop
In previous section, we learned about the `for` loop that we can use to iterate over
an iterable. In this section, we will take a look at the `while` loop.

## Understanding `while` loop
A `while` loop, unlike `for` loop, does not iterate over an iterable. This loop is used
repeatedly execute a code block until a condition is True.

The basic syntax of this loop is like so:
```py
while condition:
    # loop body here
```

Here, until `condition` could be a logical expression, a boolean or any true-like value, the
loop body would be executed until the condition is True.

Let us see an example, the following code prints out the numbers from 0 to 9:

=== "Code"

    ```py
    i = 0

    while i < 10:
        print(i)
        i = i + 1
    ```

=== "Output"

    ```
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    ```

Until the variable `i` is less than 10, the while loop is going to execute.

## Caveats
`while` loop comes with some extra caveats that must be taken into account.

### Variable Definition
In a `while` loop, the variables that are being used to control the loop (e.g. one used in
condition) must be initialized before the loop. This isn't the case in a `for` loop.

For example, in above example, since we use `i` in the condition, we must define this
variable beforehand and give it an initial value. In a `for` loop, we don't have to
do this.

=== "`while` loop"

    ```py hl_lines="1"
    i = 0

    while i < 10:
        print(i)
        i = i + 1
    ```


=== "`for` loop"

    ```py
    for i in range(10):
        print(i)
    ```

### Loop termination
`while` loop will execute until the condition is True. It is a common pitfall to run into
an "infinite loop" when using while loop.

For illustration purpose, if you run the following code, you will see that the program
prints `Hello World` repeatedly and never stops:

=== "Code"

    ```py
    while True:
        print('Hello World')
    ```

=== "Output"

    ```
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    Hello World
    [...]
    ```

In the numbers example shown above, the loop terminates because the line `i = i + 1` keeps
incrementing `i` until `i` becomes equal to `10` and the condition (`i < 10`) becomes False.

```py hl_lines="5"
i = 0

while i < 10:
    print(i)
    i = i + 1
```

If we remove that line, look at what happens:

=== "Code"

    ```py hl_lines="1"
    i = 0

    while i < 10:
        print(i)
    ```


=== "Output"

    ```
    0
    0
    0
    0
    0
    0
    0
    0
    0
    [...]
    ```

The `i` variable never updates and ultimately the `i < 10` condition is always `True` causing
the loop to run forever.

!!! note

    In a `for` loop, incrementing the loop controlling variable is handled by `range()`
    and you don't have to do that manually.

---

!!! question "Exercise"

    === "Problem"

        Write a program that repeatedly takes numbers as user input until user does not enter
        `stop`. Once `stop` is given as input, the program should output the sum of numbers
        that were input.

        Example program output:

        ``` hl_lines="1-6"
        Enter a number or type "stop": 20
        Enter a number or type "stop": 10
        Enter a number or type "stop": 5
        Enter a number or type "stop": 30
        Enter a number or type "stop": 5
        Enter a number or type "stop": stop
        Sum of given numbers is 70
        ```

        _Highlighted lines are user inputs._

    === "Solution"

        ```py
        prompt = 'Enter a number or type "stop": '
        result = 0
        value = input(prompt)

        while value != 'stop':
            result = result + int(value)
            value = input(prompt)

        print('Sum of given numbers is', result)
        ```
