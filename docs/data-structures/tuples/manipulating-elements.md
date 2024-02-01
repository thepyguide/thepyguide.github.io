# 7.2.2. Manipulating Elements
A tuple on its own is immutable meaning once it is created, the elements
of it cannot be modified directly.

There are some other ways of indirectly acheiving this behaviour
which will be discussed in this section.

## List type casting
Tuples can be converted to a list using the `list` function on the tuple. 
This type casts the tuple into a list which can be manipulated and then
reconverted into a tuple with a similar method:

=== "Code"

    ```py
    fruits = ('apple', 'banana', 'peach')

    # convert fruits tuple to a list
    fruits = list(fruits)

    # modify elements (e.g. add new element)
    fruits.append('strawberry')

    # convert back to tuple
    fruits = tuple(fruits)

    # output new tuple
    print(fruits)
    ```

=== "Output"

    ```
    ('apple', 'banana', 'peach', 'strawberry')
    ```

In order to remove elements, methods like `list.pop()` or the `del`
keyword could be used. For more information about list operations,
see [section 7.1.2. Lists: Manipulating Elements](../lists/manipulating-elements.md).

## Concatenating elements (the `+` operator)
Two or more tuples can be concatenated using the `+` operator.

=== "Code"

    ```py
    fruits = ('apple', 'banana', 'peach')
    print(fruits)

    fruits = fruits + ('strawberry', 'pineapple')
    print(fruits)
    ```

=== "Output"

    ```
    ('apple', 'banana', 'peach')
    ('apple', 'banana', 'peach', 'strawberry', 'pineapple')
    ```

---

!!! note

    Both the approaches shown above to manipulate tuple elements
    do not change the fact that **tuples are immutable**.

    In both cases, a new tuple is created every time that replaces
    the old one. The original tuple cannot be updated after its initial
    definition.

    === "Code"

        ```py
        fruits = ('apple', 'banana', 'peach')

        # convert fruits tuple to a list
        # and store in new_fruits
        new_fruits = list(fruits)

        # modify elements (e.g. add new element)
        new_fruits.append('strawberry')

        # convert new_fruits list to tuple
        new_fruits = tuple(new_fruits)

        # output new tuple
        print('new:', new_fruits)

        # output original tuple
        print('original:', fruits)
        ```

    === "Output"

        ```
        ('apple', 'banana', 'peach', 'strawberry')
        ('apple', 'banana', 'peach')
        ```

    As you can see, the original tuple remains as-is as `list(fruits)`
    returns a completely new list and doesn't change the original tuple.

    Similarly performing `tup1 + tup2` returns a new tuple with elements
    of both `tup1` and `tup2` but the content of `tup1` and `tup2` remains
    the same as original.

    === "Code"

        ```py
        tup1 = ('a', 'b', 'c')
        tup2 = ('d', 'e', 'f')
        tup3 = tup1 + tup2

        print(tup3)
        print(tup1)
        print(tup2)
        ```

    === "Output"

        ```
        ('a', 'b', 'c', 'd', 'e', 'f')
        ('a', 'b', 'c')
        ('d', 'e', 'f')
        ```
