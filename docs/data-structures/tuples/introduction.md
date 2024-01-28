# 7.2.1. Introduction to Tuples
In previous section, we learned about [List](../lists/introduction.md)
data structure. This section will cover the `tuple` data structure.

## Defining Tuples
Tuples are linear data structures that can be used to store multiple
values in a linear order under single variable, much like [lists](../lists/introduction.md). The only difference is that tuples are immutable.

A tuple can simply be defined using parantheses `()`:

```py linenums="1"
t1 = ()  # (1)!
t2 = ('apple', 'banana', 'strawberry', 'melon')  # (2)!
t3 = ('string', 45, 6.28, 9.20, True)  # (3)!
```

1. This is an empty tuple with no elements.
2. This is a tuple with 4 elements, all of same type (str)
3. This is a tuple with 5 elements, of different types.

In above code, we defined three tuples: one of them being empty, other
storing data of same data type, and the third one storing data of different
data types.

When defining a tuple, the parantheses are only required when defining
an empty tuple. Otherwise, the parantheses can be omitted:

```py
empty = ()  # (1)!
fruits = 'apple', 'banana', 'strawberry'  # (2)!
```

1. Parantheses are only required when defining empty tuple.
2. Parantheses can be omitted when defining non-empty tuples.


!!! tip

    Although it is possible to omit parantheses, it is generally considered
    a good code practice to use parantheses when defining tuples.

!!! note "Defining single element tuples"

    Be careful when defining tuple that has single element. If
    a tuple has a single element, a comma must be appended to the
    end of tuple to define a tuple.

    === "Code"

        ```py
        t1 = ('hello')
        t2 = ('hello',)

        print('t1 is a', type(t1))
        print('t2 is a', type(t2))
        ```

    === "Output"

        ```
        t1 is a <class 'str'>
        t2 is a <class 'tuple'>
        ```

    As seen in above code, omitting the comma creates a string instead
    of tuple as intended.

## Basic Features
Following are the features of tuple data structure that differentiate
it from other data structures:

- Immutable
- Ordered
- Indexable
- Allows Duplicates

### Immutable
Tuples are much like [lists](../lists/introduction.md): they are linear
data structure (sequence) and allows storing multiple items under
single variable but with one main difference, **tuples are immutable.**

This means that a tuple cannot be modified once it is created, unlike lists
that allow [manipulating the elements](../lists/manipulating-elements.md) 
after creation.

Apart from that, tuples have similar features as a list:

- [Ordered](../lists/introduction.md#ordered)
- [Indexable](../lists/introduction.md#indexable)
- [Allows Duplicates](../lists/introduction.md#allows-duplicates)

### Ordered
Similar to lists, tuples follow specific order.

=== "Code"

    ```py
    a = (1, 2, 3, 4, 5)
    b = (2, 3, 1, 5, 4)
    c = (1, 2, 3, 4, 5)

    print(a == b)
    print(c == a)
    ```

=== "Output"

    ```
    False
    True
    ```

In this code, `a` and `b` tuples have similar elements but they don't have
the same order so the two are not equal. `a` and `c` on the other hand,
have similar elements with same order so they are equal.

### Indexable
The elements of a tuple can be accessed using indexes.

=== "Code"

    ```py
    fruits = ('apple', 'banana', 'peach', 'strawberry')

    print(fruits[2])
    ```

=== "Output"

    ```
    peach
    ```

Tuples support all features of indexes that we saw in [section 4.1. Indexing Strings](../../string-operations/indexing-strings.md) as well as [slicing](../../string-operations/slicing-strings.md).

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry']

    print(fruits[-3])  # (1)!
    print(fruits[0:3])  # (2)!
    ```

    1. Indexes start from `0` (`0` pointing to first element) and [negative
       indexes](../../string-operations/indexing-strings.md#negative-indexes)
       starting from `-1` can be used to access elements from right
       hand side.

    2. Tuples can be [sliced](../../string-operations/slicing-strings.md)
       to select multiple elements from it.

=== "Output"

    ```
    banana
    ['apple', 'banana', 'peach']
    ```

### Allows Duplicates
Tuples allows duplicate elements.

```py
fruits = ('apple', 'pineapple', 'peach', 'strawberry', 'apple', 'peach')
```

In this code, `fruits[0]` and `fruits[4]` are duplicates and `fruits[2]`
and `fruits[5]` are duplicates.
