# 2.1. Variables and Data Types
In this section, we're going to look at one of the most fundamental concept of
programming, variables and data types.

## Introduction to Variables
Simply put, variables are containers that store a specific value. Each variable
has a name and a value. We can store any value to variable and when we want to
access that value again, we can simply reference that variable with its name.

For example, if we want to store the age of user, we can simply write:
```py
age = 20
```
This is the syntax of creating variables. Here, left hand side of the `=` symbol
represents the name of variable while the right hand side is the value assigned
to variable.

!!! note

    `20 = age` is not a valid syntax. Left side is always the variable name
    with right side being the value to store.

When we need the information, we can simply access it by referencing variable
name:

=== "Code"

    ```py
    age = 20
    print(age)
    ```

=== "Output"

    ```
    20
    ```

!!! info "Variable types"

    If you are coming from another language, you might be used to mentioning the
    type of variable when declaring it. In Python, the type is inferred automatically.

### Rules for variable name

There are a few rules for the name of a variable which must be followed:

- Variable name can only contain letters, numbers or underscore.
- Variable name must start with a letter or underscore.
- Variable names are case-sensitive. (e.g. `age` and `Age` are two different variables)

### Updating a variable

As the name suggest, variables value can be varied too. For example, in below snippet of
code we are first assigning the value 20 to age and after printing that, we're updating
the age variable to hold the value 30.

=== "Code"

    ```py
    age = 20
    print(age)

    age = 30
    print(age)
    ```

=== "Output"

    ```
    20
    30
    ```

When updating a variable, you can use the previous value too. For example, incrementing
the previous age by one:

=== "Code"

    ```py
    age = 20
    print(age)

    age = age + 1
    print(age)
    ```

=== "Output"

    ```
    20
    21
    ```

## Data Types
In programming, we tend to deal with different kinds of data e.g. numbers, text, decimal
numbers, dates etc.

To categorize the data, we have data types in programming. Data types are used to
represent the type or kind of data. In Python, we have four basic data types:

- `str` (string) for textual data
- `int` for integers or whole numbers
- `float` for floating point (decimal) numbers
- `bool` (boolean) for boolean values (`True` or `False`)

### Strings
The string type, `str`, is used to represent arbitrary textual values. In order to
represent a string, we enclose the given text in quotes.

=== "Code"

    ```py
    name = "Harry Potter"
    print(name)
    print(type(name))
    ```

=== "Output"

    ```
    Harry Potter
    <class 'str'>
    ```

!!! info "type() function"

    When we call the `type(X)` function, it returns the type of `X`.

Strings are used when we want to represent any textual value. It is important that we
enclose strings in quotes, either double quotes or single quotes.

```
name = "Harry Potter"
name2 = 'Harry Potter'
```

In this case, both `name` and `name2` are same. Worth noting that we cannot mix double
and single quotes. If you start a string with double quote, you must end it with a double
quote too and vice versa.

This code will raise an error because quotes are not consistent:
```py
name = "Harry Potter'
```

### Integers
When we want to represent integers i.e whole numbers, we use the `int` data type. To
represent numbers, we simply write the number as is. There is no need of enclosing them
in quotes.


=== "Code"

    ```py
    age = 20
    print(age)
    print(type(age))
    ```

=== "Output"

    ```
    20
    <class 'int'>
    ```

A common pitfall is to enclose the number in quotes which makes it of `str` data type
instead of `int` data type.

### Floating-point numbers
Floating-point numbers are simply decimal numbers. In Python, the data type to represent
these numbers is called `float`.

=== "Code"

    ```py
    pi = 3.14
    print(pi)
    print(type(pi))
    ```

=== "Output"

    ```
    3.14
    <class 'float'>
    ```

### Boolean values
Boolean value is simply either `True` or `False`. Boolean values are often used to represent
ON/OFF state. For example, if you're developing a program to control the lights remotely, you
might need a boolean value to represent the current state of lights.

In Python, we have `bool` type to represent boolean values. There are only two boolean literals,
`True` and `False`.

=== "Code"

    ```py
    lights_on = True
    print(lights_on)
    print(type(lights_on))
    ```

=== "Output"

    ```
    True
    <class 'bool'>
    ```

!!! tip

    Booleans are used in [logical expressions](../control-structures/logical-operations.md) and 
    [conditionals](../control-structures/conditionals.md). These topics are covered in later
    sections.

### Converting data types
In programming, it is important to ensure that each data is in its appropriate
data type. This is done to ensure that proper operations can be performed on the data.

For example, if you have two numeric strings `"20"` and `"30"`, you cannot add these
two until they are converted to integer type.

=== "Code"

    ```py
    n1 = "20"
    n2 = "30"
    print(n1 + n2)
    ```

=== "Output"

    ```py
    2030 # (1)!
    ```

    1. The two strings are joined together instead of expected mathematical addition
       operation.


In order to convert a data into a different type, we can call that data type
with the value that needs to be converted.

For example, we can convert a numeric string to integer:

=== "Code"

    ```py
    n1 = '20'
    n2 = '30'

    n1 = int(n1)
    n2 = int(n2)

    print(n1 + n2)
    ```

=== "Output"

    ```
    50
    ```

Similar to this, a string can also be converted to `float` and `bool`. Note that conversion
can only occur successfully if the string is convertable to the given type. That is, in case
of integers, all characters in a string are numbers.

```py
x = 'hello'
y = int(x)  # (1)!
```

1. Raises an error as `x` cannot be converted to integer.

---


!!! question "Exercise"

    === "Problem"

        **For each scenario, think of an appropriate Python data type that
        can be used.**

        1. To store the address of a user.
        2. To store the phone number of a user.
        3. To store the height of user.
        4. To store whether the user is over 18 or not.

    === "Solution"

        1. **To store the address of a user:** `str`

        Because address is a text, we must use a string to store it.

        2. **To store the phone number of a user:** `str`

        Phone numbers are a set of digits and could also include dashes
        or plus symbols, so a string.

        3. **To store the height of user:** `float`

        Heights can vary in decimals so floating point number is appropriate
        to use here.

        4. **To store whether the user is over 18 or not:** `bool`

        Since there are only two possible cases here: over 18 or not over 18,
        we can use simply use a boolean value which if True, represents that
        user is over 18 and vice versa.

## Variable Types
If you've used another statically typed programming language, you may be aware that
variables can have fixed types and once declared, they cannot change type. This isn't
the case in Python. Python is a dynamically typed language which means type can change
at runtime.

For example, in this case, we first assign age an `int` but we can update it afterwards
to hold a `str` type value. This code would execute without any errors.

```py
age = 20
age = '20'
```

In short, the type of variable isn't fixed and can change during the execution of program.
