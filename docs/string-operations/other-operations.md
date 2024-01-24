# 4.5 Other String Operations
In the previous sections, we saw some basic and common operations that
were used to deal with strings. This included:

- [Indexing Strings](./indexing-strings.md)
- [Slicing Strings](./slicing-strings.md)
- [Formatting Strings](./formatting-strings.md)

In this section, we'll see some other operations that can be performed on a 
string.

## Multiplication (the `*` operator)
Characters of a string can be multiplied using the `*` operator. As such,
the characters of string are repeated the number of times it was multiplied
with.

=== "Code"

    ```py
    string = 'abc'

    print(string * 3)
    ```

=== "Output"

    ```
    abcabcabc
    ```

It is worth noting that a new string is created on multiplication and old
string remains as is.

=== "Code"

    ```py
    string = 'abc'
    new_string = string * 3

    print(string)
    print(new_string)
    ```

=== "Output"

    ```
    abc
    abcabcabc
    ```

## `len()` function
The built-in `len()` function is used to return the length of any sequence. 
Since string is a sequence of characters too, it can return the number of
characters in the string.

=== "Code"

    ```py
    string = 'Hello Python'
    length = len(string)
    print(f'This string has {length} characters.')
    ```

=== "Output"

    ```
    This string has 11 characters.
    ```

!!! note

    Keep in mind that "space" is also considered a character.
