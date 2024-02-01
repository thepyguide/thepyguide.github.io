# 7.3.2. Manipulating Elements
Sets are mostly used for mathematical operations instead of storing
data for later use as is the case for tuples and list. Due to this,
set only provides a small set of operations to manipulate its elements.

## Adding Elements (`set.add()` method)
`set.add()` can be used to add elements to a set.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    s1.add('d')
    print(s1)
    ```

=== "Output"

    ```
    {'a', 'b', 'c', 'd'}
    ```

!!! note

    Keep in mind that order of elements isn't fixed and duplicates
    are not allowed in sets.

There are other operations that can be used to add elements such
as union operation which are covered in later section.

## Removing Elements with `set.pop()`
`set.pop()` can be used to remove a random element from the set. It
returns the removed element.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    print(s1.pop())
    print(s1)
    ```

=== "Output"

    ```
    b
    {'a', 'c'}
    ```

Unlike [`list.pop()`](../lists/manipulating-elements.md#removing-elements-methods), this method does not remove element
in a fixed order and doesn't take any index since sets are not
indexable.

Everytime the program is run, a different or random element is popped.

If set is empty, a `KeyError` is raised.

## Removing Elements with `set.remove()`
`set.remove()` removes the given item from set.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    s1.remove('a')
    print(s1)
    ```

=== "Output"

    ```
    {'b', 'c'}
    ```

`set.remove()` raises a `KeyError` if item is not found in
the set.

## Removing all elements
A set can be emptied using the `set.clear()` methods which
deletes all the elements from the set.

=== "Code"

    ```py
    s1 = {'a', 'b', 'c'}
    s1.clear()
    print(s1)
    ```

=== "Output"

    ```
    set()
    ```

!!! note

    `set()` implies empty set.
