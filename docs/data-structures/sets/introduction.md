# 7.3.1. Introduction to Sets
Sets are one of the four built-in data structures that we'll study in
this guide.

## Defining Sets
Like lists and tuples, set is also a linear data structure that stores
values in a single variable but there are two main differences between
the sets and lists or tuples:

- Sets are unordered
- Sets don't allow duplicates

We'll discuss these differnces later in this section.

In order to define a set, we have to enclose the set elements in `{}`
curly braces. Note that in order to define an empty set, we cannot
use `{}` but instead the `set()` function.

```py linenums="1"
s1 = set()  # (1)!
s2 = {'apple', 'banana', 'peach', 'strawberry'}  # (2)!
s3 = {'text', 23, 3.14, 9.20, False}  # (3)!
```

1. This is an empty set with no elements.
2. This is a set with 4 elements, all of same type (str)
3. This is a set with 5 elements, of different types.

In above code, we defined three sets: one of them being empty, other
storing data of same data type, and the third one storing data of different
data types.

!!! note "Empty set definition"

    <!-- TODO ref dict -->

    The reason why we use `set()` instead of `{}` for defining empty
    sets is because `{}` are also used to represent dictionaries so
    it becomes ambiguous on what is being defined.

## Basic Features
Following are the features of set that differentiate it from other data
structures e.g. lists and tuples.

- Unordered
- Unindexable
- No Duplicates

!!! note

    Like lists and tuples, sets are [mutable](../lists/introduction.md#mutable).

### Unordered
Sets do not follow a specific order. This can be seen when
printing sets:

```py
s1 = {'a', 'b', 'c', 'd', 'e', 'f'}
print(s1)
```

If you run the above program multiple times, you'll notice that set
is printed with different order almost everytime you run the program.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    s2 = {'b', 'c', 'a'}
    print(s1 == s2)
    ```

=== "Output"

    ```
    True
    ```

Despite defining the set with seemingly different order, the result of
this comparison is `True` because both sets have similar elements.

This is contrary to what happened in case of [lists](../lists/introduction.md#ordered) and [tuples](../tuples/introduction.md#ordered).

### Unindexable
Because sets don't have any order. They cannot be [indexed](../lists/introduction.md#indexable).

This means elements of a set cannot be accessed or replaced like lists
or tuples.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    print(s1[0])
    ```

=== "Error"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 2, in <module>
        print(s1[0])
              ~~^^^
    TypeError: 'set' object is not subscriptable
    ```

This also means that sets cannot be [sliced](../../string-operations/slicing-strings.md).

### No Duplicates
Sets do not allow duplicates. If you define a set with duplicate elements,
the duplicates are automatically ignored or discarded.


=== "Code"

    ```py
    s1 = {'a', 'b', 'c', 'a'}
    print(s1)
    ```

=== "Output"

    ```
    {'a', 'b', 'c'}
    ```

## Application
With sets being unordered and unindexable, this raises a question that
how are sets useful compared to lists and tuples?

Lists and tuples allow the stored data to be accessed while set on the
other hand, does not allow this.

Lists and tuples are used to store data and access it later while sets
are generally used to eliminate duplicates or perform mathematical set
operations on data such as union, difference and intersection.

We'll discuss this in later sections.
