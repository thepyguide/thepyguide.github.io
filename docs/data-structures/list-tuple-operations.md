# 7.4. Sequence Operations
Apart from operations covered in respective sections of each sequence
data structures, list, tuples and sets have some common operations.

!!! note

    A general term for list, tuple and set is sequence.

## Iterating using `for` loop
Elements of a sequence can be iterated over using a
[`for` loop](../control-structures/for-loop.md).

=== "Code"

    ```py
    fruits = ['apple', 'peach', 'strawberry', 'pineapple']

    for fruit in fruits:
        print(fruit)
    ```

=== "Output"

    ```
    apple
    peach
    strawberry
    pineapple
    ```

This is similar to [iterating over string characters](../control-structures/for-loop.md#iterating-over-string-characters).

!!! note

    Keep in mind that since sets are unordered, when iterating
    over a set, the order in which elements are looped is not
    fixed.

## Typecasting
We saw in [section 2.1. Variables and Data Types](../fundamentals/variables-and-data-types.md#converting-data-types) that we can
convert data from one datatype to another. This is called typecasting.

Same is the case for sequences. `list`, `tuple` and `set` are three
different data types offering a different set of operations. It is
up to you to decide that which type is suitable for a given case.

The good thing is: all of these types can be type casted into
one another.

We can call the `list()`, `tuple()` or `set()` functions to convert
a sequence to the called data type.

=== "Code"

    ```py
    list_letters = ['a', 'b', 'c']
    print(list_letters)

    tuple_letters = tuple(letters)
    print(tuple_letters)

    set_letters = set(letters)
    print(set_letters)
    ```

=== "Output"

    ```
    ['a', 'b', 'c']
    ('a', 'b', 'c')
    {'a', 'b', 'c'}
    ```

There are many reasons why you might want to convert one
type to another. For example, when you want to eliminate
duplicates, you can convert a sequence to set. Another case
is when you want to [add elements to an immutable tuple](./tuples/manipulating-elements.md#list-type-casting).

## Multiplication (the `*` operator)
Elements of a list and tuples can be multiplied using the `*` operator.
This is similar to how did [string multiplication](../../string-operations/other-operations.md#multiplication-the--operator).

=== "Code"

    ```py
    letters = ['a', 'b', 'c']
    print('before:', letters)

    letters = letters * 3
    print(f'after:', letters)
    ```

=== "Output"

    ```
    before: ['a', 'b', 'c']
    after: ['a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c']
    ```

As we can see in the output, the elements previously in the list were 
repeated 3 times when multiplied by 3.

It is important to note that when multiplying, the original list or
tuple remains the same and a new data structure is created with
updated elements.

=== "Code"

    ```py
    letters = ('a', 'b', 'c')
    print('before:', letters)

    new_letters = letters * 3
    print(f'after:', letters)
    print(f'after (new):', new_letters)
    ```

=== "Output"

    ```
    before: ('a', 'b', 'c')
    after: ('a', 'b', 'c')
    after (new): ('a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c')
    ```

!!! warning

    Multiplication is not possible for sets.

## Common Methods
Following are some commonly used methods for sequences. Other
methods have been covered in respective section of each data
structure.

??? example "`list.count()` // `tuple.count()`"

    `count()` method is used to count the number of occurences of
    an element in list or tuple.

    === "Code"

        ```py
        letters = ('a', 'b', 'c', 'd', 'b', 'e')
        print('b occurs', letters.count('b'), 'times')
        ```

    === "Output"

        ```
        b occurs 2 times
        ```

??? example "`list.index()` // `tuple.index()`"

    `index()` method is used to retrieve the index of an element.

    === "Code"

        ```py
        letters = ('a', 'b', 'c', 'd')
        print('b occurs at', letters.index('b'), 'position')
        ```

    === "Output"

        ```
        b occurs 1 position
        ```

    If the given element occurs more than once, only first occurence
    is returned.

    Optional parameters that this method takes are:

    - `start`: the index to start searching from.
    - `end`: the index to search until. (exclusive)

## Built-in Functions
Following built-in functions can be applied on sequences:

??? example "`len()`"

    `len()` function returns the size of a tuple or list i.e. number
    of elements in the data structure.

    === "Code"

        ```py
        letters = ('a', 'b', 'c', 'd', 'b', 'e')
        print(len(letters))
        ```

    === "Output"

        ```
        6
        ```

??? example "`max()` & `min()`"

    `max()` function returns the maximum value from the given
    sequence.

    === "Code"

        ```py
        values = (23, 120, 636, 10, 99)
        print(max(letters))
        ```

    === "Output"

        ```
        636
        ```

    Similarly, `min()` function returns the minimum value.

    === "Code"

        ```py
        values = (23, 120, 636, 10, 99)
        print(max(letters))
        ```

    === "Output"

        ```
        10
        ```

    Both `max()` and `min()` cannot be used on empty sequences.

??? example "`sum()`"

    `sum()` function adds the values of a sequence or iterable
    and returns the final sum.

    === "Code"

        ```py
        values = (320, 30, 10, 20)
        print(sum(letters))
        ```

    === "Output"

        ```
        380
        ```

    The elements of sequence must be integers.
