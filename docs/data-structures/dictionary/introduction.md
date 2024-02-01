# 7.5.1. Basics of Dictionary
Till now, we saw data structures that stored data as a sequence of
values that could be retrieved using indexes (except sets).

Dictionary is another data structure in Python that is different
from the rest in terms of how data is stored by dictionary.

## Defining Dictionary
In real life, we use often use language dictionaries. Similar to
language dictionaries, where each word maps to a specific definition
or meaning, Python dictionaries also are mappings that can be used
to store data as key-value pairs.

Each key in the dictionary maps to a specific value. Comparing this
to language dictionaries, key could be seen as the word and value
could be seen as its definition.

To define a dictionary, we use the `{}` curly braces. Each key-value
pair in the dictionary is separated by a `:` colon.

```py linenums="1"
d1 = {}  # (1)!
d2 = {'a': 'Apple', 'b': 'Banana', 'm': 'Mango'}  # (2)!
d3 = {'a': 0, 23: True, 3.14: 'pi'}  # (3)!
```

1. This is an empty dictionary with no items.
2. This is a dictionary with 4 items, all of same type (str)
3. This is a dictionary with 3 items, of different types.

In above code, we defined three dictionaries: one of them being empty, other
storing data of same data type, and the third one storing data of different
data types.

!!! note

    By convention, data in a dictionary are referred to as items instead
    of elements as for tuples or lists.

## Accessing Dictionary Items
To access data stored in a dictionary, a syntax similar to [indexing](../lists/introduction.md#indexable) is used.

=== "Code"

    ```py
    person = {
        'name': 'John',
        'age': 20,
        'gender': 'male',
    }

    print(person['age'])
    ```

=== "Output"

    ```
    20
    ```

As you can see that instead of using the indexes, as we did for
tuples and lists, we give the key we want to access in the `[]`
brackets. This is the way of accessing data of a dictionary.

## Basic Features
Dictionaries are different from other data structures such as list and
tuples due to the principle difference of how data is stored.

Other features of dictionaries are:

- Ordered
- Immutable Keys
- No Duplicates
- Nestable
- Mutable

### Ordered
Although accessing the data stored in the dictionary is independent
of the order, the order in which a dictionary is defined remains the
same.

Although unlike other structures, the order doesn't matter when comparing
dictionaries, the order is still preserved and when printing a dictionary,
it will appear in order in which it was defined.

=== "Code"

    ```py
    person1 = {
        'name': 'John',
        'age': 20,
        'gender': 'male',
    }

    person2 = {
        'age': 20,
        'gender': 'male',
        'name': 'John',
    }

    print(person1)
    print(person2)
    print(person1 == person2)
    ```

=== "Output"

    ```
    {'name': 'John', 'age': 20, 'gender': 'male'}
    {'age': 20, 'gender': 'male', 'name': 'John'}
    True
    ```

### Immutable Keys
The keys of the dictionary follow the rules similar to a [set](../sets/introduction.md#no-mutable-types). They must be immutable.

This means we can't use sets and lists as dictionary keys because
those are mutable types.

=== "Code"

    ```py
    d = {[0, 1]: 'A'}
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 1, in <module>
        d = {[0, 1]: 'A'}
            ^^^^^^^^^^^^^
    TypeError: unhashable type: 'list'
    ```

However, we can use tuples as dictionary keys since they are immutable.

=== "Code"

    ```py
    d = {(0, 1): 'A'}
    print(d[0, 1])
    ```

=== "Output"

    ```
    A
    ```

!!! note

    As discussed in sets topic as well, that it would be a half
    correct or incomplete statement to say that dictionary
    keys only allow "immutable types."

    This is true but the actual keys that dictionary allows are
    "hashable" types. Hashable types are those values that can
    be passed to the `hash()` function to creates a unique
    string called "hash" that Python uses internally to represent
    the keys of a dictionary.

    In other words, dictionary keys does not allow mutable types
    because they are not hashable.

There are no such restrictions on dictionary values as they can store
any arbitrary value.

## No Duplicates
Dictionary keys cannot be duplicated. When we define a duplicate key,
the old key is replaced with that key.

=== "Code"

    ```py
    d = {
        'A': 'Apple',
        'B': 'Banana',
        'A': 'Apricot',
    }
    print(d['A'])
    ```

=== "Output"

    ```
    Apricot
    ```

Dictionary values can be duplicated without any restriction. Two different
keys could store a same value.

### Nestable
Dictionaries can be nested similar to lists and tuples. This means we can
store a dictionary inside another dictionary.

=== "Code"

    ```py
    dictionary = {
        'fruits': {'A': 'Apple', 'B': 'Banana', 'P': 'Pineapple'},
        'numbers': {0: 'A', 1: 'B', 2: 'C'},
    }
    print(d['fruits']['B'])
    print(d['numbers'][1])
    ```

=== "Output"

    ```
    Banana
    B
    ```

Note that nesting is only possible in dictionary values. Keys cannot
be dictionaries as discussed earlier since they are mutable types.

### Mutable
Dictionaries, like lists, are mutable. This means the keys can be
removed, updated or added after the initial definition of dictionary.

We will cover this in [section 7.5.2. Dictionaries: Manipulating Items](./manipulating-items.md).
