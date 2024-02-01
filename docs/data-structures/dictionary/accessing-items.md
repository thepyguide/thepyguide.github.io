# 7.5.2. Accessing Items
In this section, we'll see how the items stored in a dictionary can
be accessed.

## Subscripting
We saw this syntax in the previous section too. We can pass the key
to access value of in the square brackets similar to [indexing lists](../lists/introduction.md#indexable).

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data['age'])
    ```

=== "Output"

    ```
    25
    ```

In case the key provided does not exist, a `KeyError` is raised.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data['gender'])
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 6, in <module>
        print(data['gender'])
              ~~~~^^^^^^^^^^
    KeyError: 'gender'
    ```

## `dict.get()` Method
`dict.get()` method can be used to access the value corresponding to
a key too.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.get('name'))
    ```

=== "Output"

    ```
    John
    ```

There's one difference in this method compared to the previous approach,
if the key accessed does not exist, it returns `None` instead of raising
a `KeyError`.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.get('gender'))
    ```

=== "Output"

    ```
    None
    ```

Since `gender` didn't exist, `None` was returned. Alternatively, a default
value could be provided as second parameter which is returned if key
does not exist:

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.get('name', 'No name'))
    print(data.get('gender', 'male'))
    ```

=== "Output"

    ```
    John
    male
    ```

Since `name` key existed, its value was returned and default `No name`
was ignored. In case of `gender`, the key didn't exist so default
value was returned instead.

## Accessing keys and values
A dictionary provides three methods to access its data:

### `dict.keys()`
`dict.keys()` method returns an iterable that contains the
dictionary keys.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.keys())
    ```

=== "Output"

    ```
    dict_keys(['name', 'age'])
    ```

### `dict.values()`
Similarly, `dict.values()` returns an iterable of values stored in the
dictionary.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.values())
    ```

=== "Output"

    ```
    dict_values(['John', 25])
    ```

### `dict.items()`
`dict.items()` returns an iterable that has tuples representing key-value
pairs where each tuple has two elements: key and value.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.items())
    ```

=== "Output"

    ```
    dict_items([('name', 'John'), ('age', 25)])
    ```

!!! note

    Do not confuse the returned values of each of these methods with
    ordinary [lists](../lists/introduction.md). These methods return
    a special iterable.

    It can be [indexed](../lists/introduction.md#indexable) and [iterated over](../sequence-operations.md#iterating-using-for-loop) but cannot
    be modified.

## Iterating over a dictionary
We can iterate over the items of a dictionary using a [for loop](../../control-structures/for-loop.md) and [`dict.items()`](#dictitems) method.


=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    for key, value in data.items():
        print(f'{key} in data corresponds to {value}')
    ```

=== "Output"

    ```
    name in data corresponds to John
    age in data corresponds to 25
    ```

As we saw earlier in this section, [`dict.items()`](#dictitems) returns
an iterable of key-value tuples, we are simply looping through those
tuples and [unpacking the tuple values](../tuples/unpacking-tuples.md)
into `key` and `value` variables.

!!! note

    Simply iterating over a dictionary without calling the `dict.items()`
    method loops through only the keys of the dictionary.

    === "Code"

        ```py
        data = {
            'name': 'John',
            'age': 25,
        }

        for x in data:
            print(x)
        ```

    === "Output"

        ```
        name
        age
        ```
