# 7.2.3. Unpacking Tuples
In Python, the values stored in a tuple can be assigned to different
variables. While this can be done by simply indexing the tuple and
assigning the values to variables, Python offers a more elegant and
convenient syntax to achieve this.

## Unpacking vs Indexing
Lets say we have a tuple to store the name and age of an employee:

```py
employee = ('John', 36)
```

What would be the ideal way of creating accessing the two values stored
in this tuple and assigning them to `name` and `age` variables?

If you don't know about unpacking, you most likely came up with this
solution:

```py
name = employee[0]
age = employee[1]
```

Well, that's correct too but there's a better way of doing this: Unpacking.

```py
name, age = employee
```

Now if we execute this code:

=== "Code"

    ```py
    employee = ('John', 36)
    name, age = employee

    print(name, age)
    ```

=== "Output"

    ```
    John 36
    ```

As you can see, the variables are getting the appropriate value. If
we compare the two approaches:

=== "Without Unpacking"

    ```py
    employee = ('John', 36)
    name = employee[0]
    age = employee[1]

    print(name, age)
    ```

=== "With Unpacking"

    ```py
    employee = ('John', 36)
    name, age = employee

    print(name, age)
    ```

Surely, unpacking makes things much easier. Now that we have established
the basics of unpacking, let us understand this feature in more detail.

## Understanding Unpacking
Unpacking is used to assign the values of a tuple to individual
variables.

In the example we saw before, we were assigning the values of the
tuple `employee` to `name` and `age` variables. If we look at the
syntax:

```py
name, age = ('John', 18)
```

The first value of the tuple is assigned to first variable on left
hand side and second value is assigned to second variable.

Note that the number of variables on left hand side of this assignment
expression should be same as number of items in the tuple.

The workaround for this caveat is discussed below.

## Using the `*` (asterik) operator
The `*` operator can be used as a workaround for the error discussed
above which occurs when number of items to unpack and number of unpacked
variables are not equal.

=== "Code"

    ```py
    name, age, *roles = ('John', 23, 'Developer', 'Events Manager')

    print(name)
    print(age)
    print(roles)
    ```

=== "Output"

    ```
    John
    23
    ['Developer', 'Events Manager']
    ```

As you can see, the first and second values were unpacked to `name`
and `age` variables and since `roles` has preceeding `*` operator, the
rest of the values are stored in `roles` as [list](../lists/introduction.md).

`*` can be used in beginning too. This works by unpacking values from
end of the tuple.

=== "Code"

    ```py
    *a, b, c, d = ('first', 'second', 'third', 'fourth', 'fifth')

    print(a)
    print(b)
    print(c)
    print(d)
    ```

=== "Output"

    ```
    ['first', 'second']
    third
    fourth
    fifth
    ```

The last three were unpacked to `b`, `c` and `d` variables and rest
from the start were stored in list `a`.

Similarly, the `*` in middle can be used to unpack values from start
and end and the middle ones separated as list.

=== "Code"

    ```py
    a, *b, c, d = ('first', 'second', 'third', 'fourth', 'fifth')

    print(a)
    print(b)
    print(c)
    print(d)
    ```

=== "Output"

    ```
    first
    ['second', 'third']
    fourth
    fifth
    ```

## Unpacking Function Arguments
Tuple values can also be unpacked and be passed to [function arguments](../../functions/arguments.md). This is also done using the `*` operator.

Consider the following function that multiplies two numbers:

=== "Code"

    ```py
    def product(a, b):
        return a * b

    print(product(2, 5))
    ```

=== "Output"

    ```
    10
    ```

In this case, the output is `10`. If we have a tuple with same number
of elements as arguments, we can pass it to function.

=== "Code"

    ```py
    def product(a, b):
        return a * b

    params = (2, 5)
    print(product(*params))
    ```

=== "Output"

    ```
    10
    ```

Here, the first element of tuple, `2`, is assigned to first parameter, `a`,
and second element, `5`, is assigned to second parameter, `b`.

## Unpacking Return Values
We learned in [section 5.3. Return Value](../../functions/return-value.md#returning-multiple-values) that functions can return multiple values.

These multiple return values are actually represented as tuples.

For example, the following function divides the two numbers and returns
the result of division as well as remainder:

=== "Code"

    ```py
    def divide(n, m):
        return n / m, n % m

    result = divide(5, 2)
    print(result)
    ```

=== "Output"

    ```
    (2.5, 1)
    ```

!!! note

    Recall that `%` operator is used for calculating remainder
    as discussed in [section 2.4. Mathematical Operations](../../fundamentals/mathematical-operations.md).

As you can see in output, the function is returning a tuple. We can
unpack this tuple like so:

=== "Code"

    ```py
    def divide(n, m):
        return n / m, n % m

    result, remainder = divide(5, 2)
    print(result)
    print(remainder)
    ```

=== "Output"

    ```
    2.5
    1
    ```

---

!!! tip "Unpacking with lists and other iterables"

    While most commonly, tuples are used for unpacking. Other
    sequences like lists or iterables can be unpacked too.

