# 4.3. String Methods
The `str` data type provides many useful methods that can be used to manipulate a string.

!!! note

    A method is a function that can be called on a specific data type. This concept
    is covered in detail later in the guide.

This section lists some of the commonly used and useful ones available on a string.

??? example "Case Methods"

    These methods are used to change the case of a string:

    |     Method           |                          Description                            |
    |:--------------------:|:---------------------------------------------------------------:|
    |  `str.upper()`       | Converts the string to all upper case.                          |
    |  `str.lower()`       | Converts the string to all lower case.                          |
    |  `str.capitalize()`  | Changes first character of string to upper case.                |
    |  `str.swapcase()`    | Changes lowercase characters to uppercase and vice versa.       |
    |  `str.title()`       | Changes first character of each word in string to upper case.   |

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

??? example "`str.endswith()` & `str.startswith()`"

    `endswith()` and `startswith()` is used to check whether a string begins with a specific
    string.

    === "Code"

        ```py
        text = input('Enter a text: ')
        print('Question?', text.endswith('?'))

        if text.endswith('?'):
            print('You entered a question.')
        ```

    === "Output (input: `Hello`)"

        ```
        Enter a text: Hello
        Question? False
        ```

    === "Output (input: `Hello?`)"

        ```
        Enter a text: Hello?
        Question? True
        You entered a question.
        ```

    They take two optional arguments:

    - `start` defines the starting index. By default, this is 0 (start of string)
    - `end` defines the ending index. By default, this is length of string (end of string)

    === "Code"

        ```py
        text = 'fruits: apple, strawberry, peach'

        # searches from 8th index until end of string
        print(text.startswith('apple', 8))

        # searches from 8th index to 25th index (exclusive)
        print(text.endswith('strawberry', 8, 25))
        ```

    === "Output"

        ```
        True
        True
        ```

??? example "`str.replace()`"

    `str.replace()` is used to replace a certain substring in a string with
    another string. `str.replace(old, new)` replaces `old` with `new`.

    `replace()` returns a new string with old substring replaced.

    === "Code"

        ```py
        text = 'Hello, World!'
        new = text.replace('Hello', 'Bye')
        print(new)
        ```

    === "Output"

        ```
        Bye, World!
        ```

    This method replaces all occurences of given string with new one
    but could take a `count` argument to indicate the number of occurences
    to replace.

    === "Code"

        ```py
        text = 'apple, peach, strawberry, apple, banana, apple'
        all_replaced = text.replace('apple', '[apple]')
        one_replaced = text.replace('apple', '[apple]', 1)
        print(all_replaced)
        print(one_replaced)
        ```

    === "Output"

        ```
        [apple], peach, strawberry, [apple], banana, [apple]
        [apple], peach, strawberry, apple, banana, apple
        ```

??? example "`str.count()`"

    `str.counts()` counts the number of times a substring has occured in a string.

    === "Code"

        ```py
        text = 'apple, peach, strawberry, apple, banana, apple'
        print(f'apple occured {text.count("apple")} times')
        ```

    === "Output"

        ```
        apple occured 3 times
        ```

    This method takes optional `start` and `end` parameters indicating the
    starting position to search from and ending position to end search at.

    `text.count('apple', 7)` starts searching from 7th index, `text.count('apple', 7, 14)`
    searches between 7th and 14th (exclusive) position.

    === "Code"

        ```py
        text = 'apple, peach, strawberry, apple, banana, apple'
        print(f'apple occured {text.count("apple", 7)} times after 7th index')
        print(f'apple occured {text.count("apple", 0, 32)} times between first and 32nd index')
        ```

    === "Output"

        ```
        apple occured 2 times after 7th index
        apple occured 2 times between first and 32nd index
        ```

    In above code, the first output shows the number of occurences after first occurence
    and second output shows number of occurences except the last one. 

??? example "Validation Methods"

    Some methods provided by strings are used for validation of the string. These
    are listed below:

    |     Method           |                          Description                                                                                        |
    |:--------------------:|:---------------------------------------------------------------------------------------------------------------------------:|
    |  `str.isalpha()`     | Checks if all characters in the string are alphabet letters.                                                                |
    |  `str.isalnum()`     | Checks if all characters in string are alphanumeric.                                                                        |
    |  `str.isdigit()`     | Checks if all characters in string are digits or integers.                                                                  |
    | `str.isidentifier()` | Checks if the string is a [valid variable name](../fundamentals/variables-and-data-types.md#rules-for-variable-name).       |
    |  `str.isnumeric()`   | Checks if all characters in string are numeric.                                                                             |
    |  `str.isspace()`     | Checks if all characters in string are blank spaces.                                                                        |
    |  `str.istitle()`     | Checks if all words in the string start with a capital letter.                                                              |
    |  `str.isupper()`     | Checks if all characters in the string are uppercase.                                                                       |
    |  `str.isupper()`     | Checks if all characters in the string are lowercase.                                                                       |

    Methods listed above don't take any additional parameters.

    Example:

    === "Code"

        ```py
        text1 = 'HELLO'
        text2 = 'Hello'
        print(text1.isupper())
        print(text2.isupper())
        ```

    === "Output"

        ```
        True
        False
        ```

There are many other methods provided by the `str` data type that cannot listed here. For
a list of all methods, check the official [Python documentation on this topic](https://docs.python.org/3/library/stdtypes.html#string-methods).
