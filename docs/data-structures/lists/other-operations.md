# 7.1.3. Other List Operations
In the previous section, we saw some basic and common operations that
were used to manipulate the elements of a list. This included:

- [Replacing Individual Elements](./manipulating-elements.md#replacing-single-element)
- [Replacing Multiple Elements](./manipulating-elements.md#replacing-multiple-element)
- [Concatenating Lists (the `+` operator)](./manipulating-elements.md#adding-elements--operator)
- [Adding Elements using List Methods](./manipulating-elements.md#adding-elements-methods)
- [Removing Elements using `del` keyword](./manipulating-elements.md#removing-elements-del)
- [Removing Elements using List Methods](./manipulating-elements.md#removing-elements-methods)

In this section, we'll see some other operations that can be performed
on a list.

## Iterating over a list
The elements of a list can be iterated over using `for` loop. This is
similar to how we [iterated over string characters](../../control-structures/for-loop.md#iterating-over-string-characters).

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry', 'mango', 'grapes']

    for letter in letters:
        print(letter)
    ```

=== "Output"

    ```
    apple
    banana
    peach
    strawberry
    mango
    grapes
    ```

## Multiplication (the `*` operator)
Elements of a list can be multiplied using the `*` operator. This is
similar to how did [string multiplication](../../string-operations/other-operations.md#multiplication-the--operator).

=== "Code"

    ```py
    letters = ['a', 'b', 'c']
    print('before:', letters)

    letters = letters * 3
    print(f'after:', letters)
    ```

=== "Output"

    ```
    before: ['a', 'b', 'c']
    after: ['a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c']
    ```

As we can see in the output, the elements previously in the list were 
repeated 3 times when multiplied by 3.

It is important to note that when multiplying, the original list remains
the same and a new list is created with updated elements.

=== "Code"

    ```py
    letters = ['a', 'b', 'c']
    print('before:', letters)

    new_letters = letters * 3
    print(f'after:', letters)
    print(f'after (new):', new_letters)
    ```

=== "Output"

    ```
    before: ['a', 'b', 'c']
    after: ['a', 'b', 'c']
    after (new): ['a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c']
    ```

## `len()` function
The built-in `len()` function is used to return the length of any sequence. 
Since list is a sequence too, it can return the length of a list.

=== "Code"

    ```py
    fruits = ['apple', 'banana', 'peach', 'strawberry', 'mango', 'grapes']
    length = len(fruits)
    print(f'This list has {length} elements.')
    ```

=== "Output"

    ```
    This list has 6 elements.
    ```
