# 3.3. String Methods
The `str` data type provides many useful methods that can be used to manipulate a string.

This section lists some of the commonly used and useful ones.

!!! note "Methods"

    A method is a function that can be called on a specific data type. This concept
    is covered in detail later in the guide.

## String Case Methods
These methods are used to change the case of a string:

|     Method           |                          Description                                   |
|:--------------------:|:----------------------------------------------------------------------:|
|  `str.upper()`       | Converts the string to all upper case.                                 |
|  `str.lower()`       | Converts the string to all lower case.                                 |
|  `str.capitalize()`  | Changes first character of string to upper case.                       |
|  `str.swapcase()`    | Changes lowercase characters to uppercase and vice versa.              |
|  `str.title()`       | Changes first character of each word in string to upper case.          |

=== "Code"

    ```py
    string = input('Enter some text: ')

    print('upper:', string.upper())
    print('lower:', string.lower())
    print('capitalize:', string.capitalize())
    print('swapcase:', string.swapcase())
    print('title:', string.title())
    ```

=== "Output"

    ```
    Enter some text: welcome to Python
    upper: WELCOME TO PYTHON
    lower: welcome to python
    capitalize: Welcome to Python
    swapcase: WELCOME TO pYTHON
    title: Welcome To Python
    ```

## `str.count()` and `str.index()`
`str.count()` returns the number of times a substring occurs in a string.

=== "Code"

    ```py
    string = 'apple, banana, peach, apple, strawberry, peach, apple, banana, peach'
    print('number of apples:', string.count('apple'))
    ```

=== "Output"

    ```
    number of apples: 3
    ```

It can also optionally take a starting position and ending position.

=== "Code"

    ```py
    string = 'apple, banana, peach, apple, strawberry, apple, peach, banana, peach'
    print('number of apples:', string.count('apple'))
    print('number of apples after index 7:', string.count('apple', 7))
    print('number of apples between index 0 and 27:', string.count('apple', 0, 27))
    ```

=== "Output"

    ```
    number of apples: 3
    number of apples after index 7: 2
    number of apples between index 0 and 27: 2
    ```

<!-- Listed Methods:

- str.count()
- str.index()

- str.replace()

- str.endswith()
- str.startswith()

- str.isalpha()
- str.isalnum()
- str.isdigit()
- str.isascii()
- str.isidentifier()
- str.isnumeric()
- str.isspace()
- str.istitle()
- str.isupper()
- str.split()
-->