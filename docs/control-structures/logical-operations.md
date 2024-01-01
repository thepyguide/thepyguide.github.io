# 3.3. Logical Operations
In [section 3.1. Basic Conditionals](../control-structures/conditionals.md), we learned about
`if` and `else` constructs that are used to perform operation on some condition.

In this section, we'll learn about logical operations that are used to manipulate the
conditions in `if` statements.

## The boolean type
In the [section 2.1. Variables and Data Types](../fundamentals/variables-and-data-types), we
learned about the "boolean data type" which is referred to as `bool` in Python.

For a recap, `bool` data type is used to represent a boolean value which in turn, means either
True or False. Result of logical operations is a boolean value.

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

We can use logical expressions in an `if` statement (as seen in section 3.1) to perform
an action based on whether expression evaluates to True or False.

=== "Code"

    ```py
    age = int(input('Enter an age:'))

    if age >= 18:
        print('You can drive.')
    else:
        print('You cannot drive.')
    ```

=== "Output (Input: 23)"

    ```
    Enter an age: 23
    You can drive.
    ```

=== "Output (Input: 18)"

    ```
    Enter an age: 18
    You can drive.
    ```

=== "Output (Input: 12)"

    ```
    Enter an age: 12
    You cannot drive.
    ```

Here, `age >= 18` is the logical expression and the print statement is only executed when
this expression evaluates to True.

## AND, OR and NOT operators
In some cases, you have multiple expressions that you have to check for.

### AND operator
`and` is a logical operator that checks whether all conditions are True. If any
one or more of the conditions are not satisfied, the result is False.

As an example, in order for user to be able to drive, following conditions must be satisfied:

- the user must be 18 years or above
- the user must have above 6.5 on driving test

We can represent this like so:

=== "Code"

    ```py
    age = int(input('Enter your age: '))
    driving_test_score = float(input('Enter your driving test score: '))

    if age >= 18 and driving_test_score > 6.5:
        print('You can drive.')
    else:
        print('You cannot drive.')
    ```

=== "Output (age: 18, score: 10)"

    ```
    Enter your age: 18
    Driving test score: 10
    You can drive.
    ```

    Here, `driving_test_score >= 6.5` expression results in `True` and `age >= 18`
    results in `True`. The overall expression results in `True` because both expressions
    are `True`.

=== "Output (age: 12, score: 10)"

    ```
    Enter your age: 12
    Driving test score: 10
    You cannot drive.
    ```

    Here, `driving_test_score >= 6.5` expression results in `True` but `age >= 18`
    results in `False`. The overall expression results in `False`.

=== "Output (age: 23, score: 6)"

    ```
    Enter your age: 23
    Driving test score: 6
    You cannot drive.
    ```

    Here, `driving_test_score >= 6.5` expression results in `False` but `age >= 18`
    results in `True`. The overall expression results in `False`.

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
        print('Passed test?', passed_test)
        print('Can drive?', over_18 and passed_test)
        ```

    === "Output"

        ```
        Over 18? True
        Passed test? False
        Can drive? False
        ```

### OR operator
The `or` operator evaluates to True if **any one or more** of the given expressions are True.

For example, lets say a customer is only eligible for discount if he or she spends at least 100$ 
_or_ if the customer has shopped at store more than 10 times.

=== "Code"

    ```py
    amount_spent = int(input('Enter amount spent shopping: '))
    old_customer = input('Are you an old customer? ')

    if amount_spent > 150 or old_customer == 'yes':
        print('Customer gets a discount.')
    else:
        print('Discount not applied.')
    ```

=== "Output #1"

    ```
    Enter amount spent shopping: 250
    Are you an old customer? yes
    Customer gets a discount.
    ```

    Here, `amount_spent > 150` is `True` and `old_customer == 'yes'` is also `True` so
    overall expression is `True`.

=== "Output #2"

    ```
    Enter amount spent shopping: 50
    Are you an old customer? yes
    Customer gets a discount.
    ```

    Here, `amount_spent > 150` is `False` but `old_customer == 'yes'` is `True` so
    overall expression is `True`.

=== "Output #3"

    ```
    Enter amount spent shopping: 40
    Are you an old customer? no
    Discount not applied.
    ```

    Here, `amount_spent > 150` is `False` and `old_customer == 'yes'` is also `False` so
    overall expression is `False`.

---

Simply put, if you test the following logical expressions, you'd get the mentioned
result:

- `True and True` evaluates to `True`
- `True and False` evaluates to `False`
- `False and False` evaluates to `False`
- `True or True` evaluates to `True`
- `True or False` evaluates to `True`
- `False or False` evaluates to `False`

!!! info

    - For `and`, if all expressions are True, result is True. If any expression is
      False, result is False.

    - For `or`, if any expression is True, result is True. If all expressions are False,
      result is also False.

### NOT operator
We also have a `not` operator which simply inverts the given boolean value. That is,
`not True` evaluates to `False`. `not False` evaluates to `True`.

For example, the expression in code below is `True` only when X is not greater than
Y (either X < Y or X = Y):

=== "Code"

    ```py
    X = int(input('X: '))
    Y = int(input('Y: '))
    print('X is not greater than Y:', not (X > Y))
    ```

=== "Output (X: 20, Y: 30)"

    ```
    X: 20
    Y: 30
    X is not greater than Y: True
    ```

=== "Output (X: 30, Y: 20)"

    ```
    X: 30
    Y: 20
    X is not greater than Y: False
    ```

This expression is just an equivalent of `X <= Y`.
