# 7.1.2. Manipulating Elements
Data stored in a list can be modified after list has been initially
defined. Let us have a look at some ways of doing that.

## Replacing Single Element
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

## Replacing Multiple Elements
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

## Adding Elements (`+` operator)
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

## Adding Elements (methods)
Other ways of adding elements is using the methods provided by list
data type: `list.append()`, `list.extend()` and `list.insert()`.

### `list.extend()`
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

### `list.append()`
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

### `list.insert()`
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

## Removing Elements (`del`)
List elements can be removed using their indexes using the `del` keyword.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    print('before:', fruits)

    del fruits[1]
    print('after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach']
    after: ['apple', 'peach']
    ```

<!-- TODO: page for del kw -->

!!! note

    The `del` keyword is used to delete any object in Python. If we
    use `del` on a variable, that variable is deleted.

    ```py
    a = 1
    del a
    print(a)  # NameError: 'a' is not defined
    ```

## Removing Elements (methods)
The `list` data type provides many methods that can be used to remove elements
from a list.

### `list.pop()`
`list.pop()` works in a similar way as the `del` operator: it removes the element
using its index. The only difference is that the removed element is also returned
by this method.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    print('before:', fruits)

    removed = fruits.pop(1)
    print(f'after removing {removed}:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach']
    after removing banana: ['apple', 'peach']
    ```

`fruits.pop(1)` returned the removed element, `'banana'`.

If no argument is passed in `list.pop()`, the last element of the list (from
right hand side) is removed:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    print('before:', fruits)

    removed = fruits.pop()
    print(f'after removing {removed}:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach']
    after removing peach: ['apple', 'banana']
    ```

### `list.remove()`
`list.remove()` takes any value as parameter and removes that value from the
list:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    print('before:', fruits)

    fruits.remove('banana')
    print(f'after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach']
    after: ['apple', 'peach']
    ```

Worth noting that if the given value appears more than once in the list, only
the first occurence is removed:

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'banana']
    print('before:', fruits)

    fruits.remove('banana')
    print(f'after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'banana']
    after: ['apple', 'peach', 'banana']
    ```

In case the passed value is not in the list, a `ValueError` is raised.

### `list.clear()`
`list.clear()` is a rather nuclear option. This method deletes all elements
of the list and makes it empty.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach']
    print('before:', fruits)

    fruits.clear()
    print(f'after:', fruits)
    ```

=== "Output"

    ```
    before: ['apple', 'banana', 'peach', 'banana']
    after: []
    ```

