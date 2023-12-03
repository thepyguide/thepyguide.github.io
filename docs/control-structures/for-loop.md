# 3.5. The "for" Loop
Sometimes, we want to repeatively execute some piece of code. To do this, we use loops. The
next few sections of the guide will cover how loops work in Python.

In this section, we'll learn about the `for` loop.


## Understanding `for` loop
A `for` loop is used to iterate through an iterable. The syntax for this loop is like so:

```py
for variable in iterable:
    # ... code to execute here ...
```

For example, here's a really basic for-loop that prints the first 10 numbers starting from 0
and ending at 9.

=== "Code"

    ```py
    for num in range(10):
        print(num)
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

Don't worry if you don't understand what is happening here as we'll go through that in a
minute.

If you're a beginner, you might find the terms "iterating", "iteration" and "iterable"
confusing so lets see what each of these terms exactly mean.

## Basic loop terminologies
There are some terms that are used when talking about loops, or repetition in general. It
is important that you know the meaning of these terms as these terms are used frequently
in programming.

These terms are explained in simple words below. Note that these are not technical
definitions.

- **Iterating** means going through or processing the elements present in an iterable

- **Iterable** could be a string of characters, range of numbers (as shown above),
  some data structure, or any other sequence that could have many elements.

## Iterating over range of numbers
The most basic and common use of a for loop is iterating over a range of numbers. To
do so, we use the `range()` function.

We've already seen an example above that uses this `range()` function but let us understand
it more deeply.

=== "Code"

    ```py linenums="1"
    for num in range(10):
        print(num)
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

To shed some light on the syntax,

- `range(10)` is the iterable here that can iterate from `0` to `9`.
- `num` is the variable which is assigned the number being processed on each iteration.
- `print(num)` is the body of loop which is executed on each iteration (loop body could be
  multiple lines of code too)

When we execute above code, we're basically telling Python to go through the items
in the `range(10)` iterable (numbers from 0 to 9) and for each item, assign the item
to `num` variable and execute the body of loop (line 2).

Each execution of the loop body (line 2) is referred to as a single **iteration** and when
we say "first iteration", we're referring to first execution of the loop, when `num` is set
to `0`. There are a total of 10 iterations i.e the loop body is executed ten times
(from `num=0` to `num=9`).

### Manipulating `range()` function
The `range()` function can be used in a number of ways to modify the range of numbers
that are iterated through.

- **`range(end)` iterates from `0` to `end - 1` (upper bound, `end`, is exclusive)**

    === "Code"

        ```py
        for num in range(10):
            print(num)
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

- **`range(start, end)` iterates from `start` to `end - 1` (upper bound, `end`, is exclusive)**

    === "Code"

        ```py
        for num in range(1, 11):
            print(num)
        ```

    === "Output"

        ```
        1
        2
        3
        4
        5
        6
        7
        8
        9
        10
        ```

    !!! tip

        `range(10)` and `range(0, 10)` are both equivalent. In former, the `start`
        is automatically defaulted to `0`.

- **`range(start, end, step)` iterates from `start` to `end - 1` with an increment of
  `step` on each iteration**

    On every iteration, `step` is added to previous number. By default (when no
    step is provided), the `step` is set to 1.

    === "Code"

        ```py
        for num in range(0, 10, 2):
            print(num)
        ```

    === "Output"

        ```
        0
        2
        4
        6
        8
        ```

    It is also possible to move backwards (descending range) by providing step as `-1`

    === "Code"

        ```py
        for num in range(10, 0, -1):
            print(num)
        ```

    === "Output"

        ```
        10
        9
        8
        7
        6
        5
        4
        3
        2
        1
        ```

!!! info "Exclusive Upper Bound"

    Remember! the upper bound or `end`, in `range()` is always exclusive. This means:

    - `range(10)` iterates from 0 to 9.
    - `range(1, 10)` iterates from 1 to 9.
    - `range(0, 10, 2)` has elements 0, 2, 4, 6, 8 while `range(0, 12, 2)` has elements
      0, 2, 4, 6, 8, 10.

!!! tip "Repeatedly executing a code"

    If you repeatedly want to execute same block of code, you can do this using the same
    `range()` approach:

    === "Code"

        ```py
        for num in range(10):  # execute 10 times
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
        ```

## Iterating over string characters
If we have a string, we can use a for loop to iterate over the characters of that
string.

=== "Code"

    ```py
    for char in 'London':
        print(char)
    ```

=== "Output"

    ```
    L
    o
    n
    d
    o
    n
    ```

<!-- sep -->

=== "Code"

    ```py
    word = input('Enter a word: ')

    for char in word:
        print(char)
    ```

=== "Output"

    ``` hl_lines="1"
    Enter a word: Hello
    H
    e
    l
    l
    o
    ```

---

## Exercise
We'll learn about more iterables that for loop can iterate over later in the guide
such as data structures but for now, here's a simple task for you:

!!! question "Exercise"

    === "Problem"

        Take two numbers as input and output the times table of first number
        from 1 to second number.

        **You must use a `for` loop for this problem.**

        Example output:
        ``` hl_lines="1 2"
        Enter a number: 2
        Enter the end point: 12

        2 * 1 = 2
        2 * 2 = 4
        2 * 3 = 6
        2 * 4 = 8
        2 * 5 = 10
        2 * 6 = 12
        2 * 7 = 14
        2 * 8 = 16
        2 * 9 = 18
        2 * 10 = 20
        2 * 11 = 22
        2 * 12 = 24
        ```

        _Highlighted lines are the input._

    === "Solution"

        ```py
        num = int(input('Enter a number: '))
        end = int(input('Enter the end point: '))

        for x in range(1, end + 1):  # (1)!
            result = num * x
            print(num, '*', x, '=', result)  # num * x = result
        ```

        1. The upper bound, `end`, in `range(start, end)` is exclusive so we add `1`
           to the `end` variable to include `end` in our output.
