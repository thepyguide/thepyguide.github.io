# 3.1. Logical Operations
In this brief section, we'll learn how this data type is useful to us and how we can
produce some "logical operations" that either evaluate to "True" or "False".

## The boolean type
In the [section 2.1. Variables and Data Types](../fundamentals/variables-and-data-types), we
learned about the "boolean data type" which is referred to as `bool` in Python.

For a recap, `bool` data type is used to represent a boolean value which in turn, means either
True or False.

## Basic logical operations
Let us understand this with an example, if we have a variable `age` representing the age
of a user, we can check whether the user can drive or not by checking whether the age
is above 18 or not.

=== "Code"
```py
age = 12
print('Can user drive?', age > 18)
```

=== "Output"
```
Can user drive? False
```

If we change the value of `age` to say, `23`, we get:

=== "Code"

    ```py
    age = 23
    print('Can user drive?', age > 18)
    ```

=== "Output"

    ```
    Can user drive? True
    ```

Here, `age > 18` is a logical expression. This expression uses the `>` logical operator
to check whether the age is greater than `18`.

A logical expression is formed using logical operators and can either evaluate to
True or False. The basic logical operators that can be used are:

- `==` (Equals to)
- `!=` (Not Equals to)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

=== "Code"

    ```py
    age = int(input('Enter an age:'))

    print('Is 18?', age == 18)
    print('Not 18?', age != 18)
    print('Above 18?', age > 18)
    print('Above 18 or Is 18?', age >= 18)
    print('Below 18?', age < 18)
    print('Below 18 or Is 18?', age <= 18)
    ```

=== "Output (Input: 18)"

    ```
    Enter an age: 18
    Is 18? True
    Not 18? False
    Above 18? False
    Above 18 or Is 18? True
    Below 18? False
    Below 18 or Is 18? True
    ```


=== "Output (Input: 12)"

    ```
    Enter an age: 12
    Is 18? False
    Not 18? True
    Above 18? False
    Above 18 or Is 18? False
    Below 18? True
    Below 18 or Is 18? True
    ```


=== "Output (Input: 23)"

    ```
    Enter an age: 23
    Is 18? False
    Not 18? True
    Above 18? True
    Above 18 or Is 18? True
    Below 18? False
    Below 18 or Is 18? True
    ```

In above code, we change the value of `age` by giving different input each time to play with
the output of each expression.

## AND, OR, NOT operations
In some cases, you have multiple expressions that you have to check for. For example, in
order for some to be able to drive:

- the user must be 18 years or above
- the user must have at least a score of 7 on driving test

We can represent this like so:

=== "Code"

    ```py
    age = 23
    driving_test_score = 9.5

    print('Can user drive?', age >= 18 and driving_test_score > 7)
    ```

=== "Output"

    ```
    Can user drive? True
    ```

`and` is a logical operator that checks whether all conditions are True. If any
of the conditions listed above are not satisfied, the result is False.

!!! tip

    A logical expression produces a boolean value which can also be assigned
    to a variable. This is particularly useful when we have large expressions
    which could become confusing.

    === "Code"

        ```py
        age = 23
        driving_test_score = 6.5

        over_18 = age >= 18
        passed_test = driving_test_score > 7

        print('Over 18?', over_18)
        print('Passed test?', over_18)
        print('Can drive?', over_18 and passed_test)
        ```

    === "Output"

        ```
        Over 18? True
        Passed test? False
        Can drive? False
        ```

Similarly, we have `or` operator that evaluates to True if **any** one of the
given condition is True. For example, lets say a customer is only eligible
for discount if he or she spends at least 100$ _or_ if the customer has shopped
at store before.

=== "Code"

    ```py
    amount_spent = 150
    old_customer = False

    print('Discount applicable?', amount_spent > 150 or old_customer)
    ```

=== "Output"

    ```
    Discount applicable? True
    ```

Note that despite `old_customer` being False, the customer was still given the
discount because more than 100$ were spent.

Simply put, if you test the following logial expressions, you'd get the mentioned
result:

- `True and True` evaluates to `True`
- `True and False` evaluates to `False`
- `False and False` evaluates to `False`
- `True or True` evaluates to `True`
- `True or False` evaluates to `True`
- `False or False` evaluates to `False`

!!! note

    We can use `and` and `or` for as many expressions as we like.

    For example, `e1 and e2 and e3` means that `e1`, `e2`, `e3`, all
    have to be True for result to be True.

!!! info

    - For `and`, if all expressions are True, result is True. If any expression is
      False, result is False.

    - For `or`, if one or more expression are True, result is True. If all
      expressions are False, result is also False.

We also have a `not` operator which simply inverts the given boolean value. That is,
`not True` evaluates to `False`. `not False` evaluates to `True`.

For example, the expression in code below is `True` only when age is less than 18:

=== "Code"

    ```py
    age = int(input('Enter age: '))
    print('age is not greater than 18:', not age >= 18)
    ```

=== "Output (Input: 23)"

    ```
    Enter age: 23
    age is not greater than 18: False
    ```

=== "Output (Input: 12)"

    ```
    Enter age: 12
    age is not greater than 18: True
    ```

=== "Output (Input: 18)"

    ```
    Enter age: 18
    age is not greater than 18: True
    ```

This expression is just an equivalent of `age < 18`.

----

## Application of logical expressions
You may ask, how are logical expressions and their result useful to us? We're glad you
asked. Logical expressions form the base for a much important and fundamental concept.

In the next section, you'd learn about **conditional statements**. These statements would
use result of logical expressions to make decisions and make your programs even more
interesting.

_**More information in the next section!**_
