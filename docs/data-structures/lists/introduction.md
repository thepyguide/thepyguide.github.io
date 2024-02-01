# 7.1.1. Basics of Lists
In programming, we need a way of storing and representing large and
complex data. This is when data structures come into play.

In this chapter, we'll learn about various built-in data structures
in Python, starting with lists!

## Defining Lists
Lists are used to store a sequence of values of either same or different
data types under a single variable.

A list is defined using square brackets `[]`:

```py linenums="1"
l1 = []  # (1)!
l2 = ['apple', 'banana', 'peach', 'strawberry']  # (2)!
l3 = ['text', 23, 3.14, 9.20, False]  # (3)!
```

1. This is an empty list with no elements.
2. This is a list with 4 elements, all of same type (str)
3. This is a list with 5 elements, of different types.

In above code, we defined three lists: one of them being empty, other
storing data of same data type, and the third one storing data of different
data types.

!!! note

    If you're using the web browser version of this guide, click on
    the each `+` icon in the code to view detail of list defined on
    that line.

## Basic Features
Lists have some characteristic features that distinguish them
from other linear data structures provided by the language:

- Ordered
- Indexable
- Allows Duplicates
- Nestable
- Mutable

### Ordered
All lists have follow a specific order.

=== "Code"

    ```py
    a = [1, 2, 3, 4, 5]
    b = [2, 3, 1, 5, 4]
    c = [1, 2, 3, 4, 5]

    print(a == b)
    print(c == a)
    ```

=== "Output"

    ```
    False
    True
    ```

In this code, `a` and `b` lists have similar elements but they don't have
the same order so two lists are not equal. `a` and `c` on the other hand,
have similar elements with same order so the two lists are equal.

### Indexable
Each element stored in a list can be accessed by its index. We learned
about indexes in [section 4.1. Indexing Strings](../../string-operations/indexing-strings.md).

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']

    print(fruits[2])
    ```

=== "Output"

    ```
    peach
    ```

All the rules about indexes we saw in [section 4.1. Indexing Strings](../../string-operations/indexing-strings.md) are applicable on lists too:

Indexes start from `0` (`0` pointing to first element) and negative
indexes starting from `-1` can be used to access elements from right
hand side.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']

    print(fruits[-3])
    ```

=== "Output"

    ```
    banana
    ```

Since list elements are represented by indexes, this also means that
lists can be sliced similar to strings.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']

    print(fruits[0:3])
    ```

=== "Output"

    ```
    ['apple', 'banana', 'peach']
    ```

`list[n:m]` returns a new list starting from element on `n` index in
original `list` up until element on `m - 1` index (upper bound is
exclusive).

For more information on slicing, see [section 4.2. Slicing Strings](../../string-operations/slicing-strings.md).

### Allows Duplicates
Lists allow duplicate elements to be stored.

=== "Code"

    ```py
    fruits = [
        'apple',
        'peach',
        'banana',
        'peach',
        'strawberry',
        'peach',
        'apple'
    ]

    print(fruits)
    ```

=== "Output"

    ```
    ['apple', 'peach', 'banana', 'peach', 'strawberry', 'peach', 'apple']
    ```

In this case, `fruits[0]` and `fruits[6]` are duplicates and `fruits[1]`,
`fruits[3]` and `fruits[5]` are duplicates.

### Nestable
Lists can be nested. This means we can store a list inside another list.

=== "Code"

    ```py
    l = [
        [0, 1, 2],
        ['a', 'b', 'c'],
    ]

    print(l[1][2])
    ```

=== "Output"

    ```
    c
    ```

In this code, we're first accessing the second element of `l` which
is in turn another list `['a', 'b', 'c']` then we're indexing the second
list accessing the third element.

There is no restriction on how deep we can go with nesting:

=== "Code"

    ```py
    l = [
            [0, 1, 2],
            [
                'a', 'b',
                ['c', 'd'],
            ],
        ]

        print(l[1][1][0])
    ```

=== "Output"

    ```
    c
    ```

Undoubtedly this code looks tedious and confusing but we're simply storing
two lists in `l` and the second list has another list nested in it.

### Mutable
Lists is a mutable data structure. This means the items in a list can
be updated after the list has been defined initially.

We'll see how lists are updated and modified in the later section.

!!! note

    Up until now, we had only seen immutable types that could not be
    modified once created. For example, integers, strings, floats
    and booleans are all immutable types whose value cannot be changed
    after definition.

    Lists is the first mutable type that we're discussing in this guide
    with many more to come in sections ahead.
