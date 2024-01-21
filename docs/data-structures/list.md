# 7.1. Lists
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
about indexes in [section 4.1. Indexing Strings](../string-operations/indexing-strings.md).

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']

    print(fruits[2])
    ```

=== "Output"

    ```
    peach
    ```

All the rules about indexes we saw in [section 4.1. Indexing Strings](../string-operations/indexing-strings.md) are applicable on lists too:

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

For more information on slicing, see [section 4.2. Slicing Strings](../string-operations/slicing-strings.md).

### Mutable
Lists is a mutable data structure. This means the items in a list can
be updated after the list has been defined initially.

We'll see how lists are updated and modified later in this section.

!!! note

    Up until now, we had only seen immutable types that could not be
    modified once created. For example, integers, strings, floats
    and booleans are all immutable types whose value cannot be changed
    after definition.

    Lists is the first mutable type that we're discussing in this guide
    with many more to come in sections ahead.

## Manipulating Lists
Data stored in a list can be modified after list has been initially
defined. Let us have a look at some ways of doing that.

### Replacing Single Element
Elements in a list can be replaced using the indexes.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']
    print('before:', fruits)

    fruits[1] = 'grapes'
    print('after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'strawberry']
    after: ['grapes', 'banana', 'peach', 'strawberry']
    ```

Note that it isn't possible to add additional elements using indexes:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']
    print('before:', fruits)

    fruits[4] = 'grapes'
    print('after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'strawberry']
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 4, in <module>
        fruits[4] = 'grapes'
        ~~~~~~^^^
    IndexError: list assignment index out of range
    ```

Since list only has four elements, maximum index is 3 and we're trying
to assign to 4th index which isn't allowed.

### Replacing Multiple Elements
It is also possible to replace multiple elements using slices:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry', 'mango', 'grapes']
    print('before:', fruits)

    fruits[1:4] = ['BANANA', 'PEACH', 'STRAWBERRY']
    print('after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'strawberry']
    after: ['apple', 'BANANA', 'PEACH', 'STRAWBERRY', 'mango', 'grapes']
    ```

Again, the upper bound is exclusive in this case so in order to replace
elements from index 1 to index 3, we have to provide `1:4`.

Note however that it isn't necessarily important for list being
replaced to be of same size as provided index range. Additional
elements are adjusted automatically:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry', 'mango', 'grapes']
    print('before:', fruits)

    fruits[1:4] = ['BANANA', 'PEACH', 'STRAWBERRY', 'WATERMELON']
    print('after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'strawberry']
    after: ['apple', 'BANANA', 'PEACH', 'STRAWBERRY', 'WATERMELON', 'mango', 'grapes']
    ```

In this case, `WATERMELON` was the additional element.

### Adding Elements (`+` operator)
Elements can be added to the list in various ways.

First way is by concatenating lists. Two lists can be added such
that the elements of second list (the one on right of `+` operator)
are appended to the first list.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    new_fruits = fruits + ['strawberry', 'mango']

    print(new_fruits)
    ```

=== "Output"

    ```
    ['apple', 'banana', 'peach', 'strawberry', 'mango']
    ```

A new list is created everytime `+` is used between two lists.

### Adding Elements (methods)
Other ways of adding elements is using the methods provided by list
data type: `list.append()`, `list.extend()` and `list.insert()`.

#### `list.extend()`
`list.extend()` is essentially same as using the `+` operator.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    fruits.extend(['strawberry', 'mango'])

    print(fruits)
    ```

=== "Output"

    ```
    ['apple', 'banana', 'peach', 'strawberry', 'mango']
    ```

One caveat about `.extend()` is that passed argument isn't necessarily
supposed to be a list. It could be any iterable, even a string too. This
isn't the case in using `+` operator.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    fruits.extend('mango')

    print(fruits)
    ```

=== "Output"

    ```
    ['apple', 'banana', 'peach', 'm', 'a', 'n', 'g', 'o']
    ```

Another thing to note is that `+` creates a new list with updated
elements while `.extend()` updates the old list instead of creating
new one. This is called in-place update operation.

#### `list.append()`
`list.append()` on the other hand is used to add singular elements
to the end of list.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']

    fruits.append('mango')
    print('appended mango:', fruits)

    fruits.append('strawberry')
    print('appended strawberry:', fruits)
    ```

=== "Output"

    ```
    appended mango: ['apple', 'banana', 'peach', 'mango']
    appended strawberry: ['apple', 'banana', 'peach', 'mango', 'strawberry']
    ```

#### `list.insert()`
Finally, we have `list.insert()` method which is used to insert
elements at a specific index.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']

    fruits.insert(0, 'mango')
    print('insert mango at start:', fruits)

    fruits.insert(2, 'strawberry')
    print('insert strawberry at index 2:', fruits)
    ```

=== "Output"

    ```
    insert mango at start: ['mango', 'apple', 'banana', 'peach']
    insert strawberry at index 2: ['mango', 'apple', 'strawberry', 'banana', 'peach']
    ```

### Removing Elements
