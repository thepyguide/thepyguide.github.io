# 7.5.3. Manipulating Items
In this section, we'll see some ways of manipulating the items of a
dictionary data structure.

## Setting Key Values
The most basic way of adding an element to a dictionary is by
setting the key to its value.

=== "Code"

    ```py
    data = {}
    data['name'] = 'John'
    data['age'] = 25

    print(data)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 25}
    ```

Note that if the key already exists in the dictionary, its value
is updated with the new one.

=== "Code"

    ```py
    data = {}

    data['name'] = 'John'
    data['age'] = 25
    print(data)

    data['name'] = 'Alex'
    print(data)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 25}
    {'name': 'Alex', 'age': 25}
    ```

## Updating dictionary
A dictionary can be updated with the new one using the `dict.update()`
method. It takes another dictionary which is merged with original one.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    data.update({'gender': 'male', 'role': 'Manager'})
    print(data)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 25, 'gender': 'male', 'role': 'Manager'}
    ```

If a key in new dictionary already exists in original one, its value
in original is updated with new one.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    data.update({'gender': 'male', 'name': 'Alex'})
    print(data)
    ```

=== "Output"

    ```
    {'name': 'Alex', 'age': 25, 'gender': 'male'}
    ```

`dict.update()` can also take any iterable with key value pairs (a
sequence with two values, first one being the key and second representing
the value).

For example, we're passing a list of two key-value pairs here:

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    data.update([('gender', 'male'), ('role', 'Manager')])
    print(data)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 25, 'gender': 'male', 'role': 'Manager'}
    ```

## Deleting Items (`del` Keyword)
The `del` keyword can be used to remove a key from the dictionary.


=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    del data['name']
    print(data)
    ```

=== "Output"

    ```
    {'age': 25}
    ```

The key must exist. If not, a `KeyError` is raised.

## Deleting Items (Methods)
`dict.pop()` removes an item from the dictionary by its key name and
returns the value.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.pop('age'))
    print(data)
    ```

=== "Output"

    ```
    25
    {'name': 'John'}
    ```

If the key does not exist, it raises a `KeyError` unless a default value
is provided as second parameter.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.pop('gender', 'male'))
    print(data)
    ```

=== "Output"

    ```
    male
    {'name': 'John', 'age': 25}
    ```

Since `gender` key didn't exist, the default value provided as second
parameter was returned instead of raising `KeyError`.

There is also a `dict.popitem()` that removes the most recently added
item. It returns a two-value tuple in which first item is the key removed
and second item is the value.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data.popitem())
    print(data)
    ```

=== "Output"

    ```
    ('age', 25)
    {'name': 'John'}
    ```

Note that since `age` was the last element of dictionary, it was removed.

!!! note

    In Python versions below 3.7, a random item was removed by this
    method because dictionaries were not [ordered](../dictionary/introduction.md#ordered).

## Clearing Items
`dict.clear()` method takes the destructive approach and deletes all
items from a dictionary.

=== "Code"

    ```py
    data = {
        'name': 'John',
        'age': 25,
    }

    print(data)

    data.clear()
    print(data)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 25}
    {}
    ```
