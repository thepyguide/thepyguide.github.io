# 4.2. Slicing Strings
In this section, we'll discuss how strings can be sliced to produce substrings.

## Understanding syntax
String slicing is used to select some characters from a string to form a new smaller string 
(substring).

The syntax for string slicing is:
```
string[start:end:step]
```

- `start` is the index of character to start slicing from
- `end` is the index of character to slice until (exclusive)
- `step` is the increment in `start` for each subsequent character

Note that each of three arguments may be omitted and would be given a default value
automatically.

!!! note "Zero based index"

    Keep in mind, as mentioned in previous section, indexes always start from 0.

## Basic Usage
`string[start:end]` returns a substring of `string` starting from character at `start` index
until character at `end - 1` index.

=== "Code"

    ```py
    string = 'Hello World'
    print(string[6:11])
    ```

=== "Output"

    ```
    World
    ```

Note that in `string[start:end]`, `step` defaults to 1.

!!! note "Exclusive upper index"

    The upper index, `end`, in `string[start:end]` is exclusive. This means `string[6:11]` starts
    from 6th index up until 10th index and doesn't include 11th index.

## Substring from first character
When index before first colon is omitted, it defaults to 0.

`string[:end]` returns a substring of `string` starting from first character until character
on the `end - 1` index.

This is equivalent to `string[0:end]` (`start` given the default value)

=== "Code"

    ```py
    string = 'Hello World'
    print(string[:6])
    ```

=== "Output"

    ```
    Hello
    ```


## Substring till last character
When index after first colon is omitted, it defaults to 0.

`string[start:]` returns a substring of `string` starting from `start` index until last
character.

This is equivalent to `string[start:length_of_string]` (`end` given the default value of length
of string).

=== "Code"

    ```py
    string = 'Hello World'
    print(string[:6])
    ```

=== "Output"

    ```
    Hello
    ```

## The `step` parameter
`step` defines the increment in `start` for each subsequent character in the string.

`string[start:end:step]` starts from `start` index and for each next index, adds `step` to
the `start` until `end` is reached.

For example, if our `string` is `Hello World` and we slice the string using `string[0:11:2]`,

- Start from `0` (start) index so first character in substring is `H`
- Add `2` (step) to `0` (start) and second character is at index `2`, `l`
- Add `2` (step) to `2` (previous index) and third character is at index `4`, `o`
- Add `2` (step) to `4` (previous index) and third character is at index `6`, `W`
- Repeat until `11` (end) is reached so final character would be at index `10`, `d`

=== "Code"

    ```py
    string = 'Hello World'
    print(string[0:11:2])
    ```

=== "Output"

    ```
    HloWrd
    ```

`string[0::2]` also produces the same result where `end` is given the default
value of `11` (length of string).

!!! note

    `step` cannot be zero but could be negative (to move in reverse order).

## Negative indexes
[Negative indexes](./indexing-strings.md#negative-indexes) can be used while slicing to
extract characters from end of string.

=== "Code"

    ```py
    string = 'Hello World'
    print(string[-10:-6])
    ```

=== "Output"

    ```
    ello
    ```

