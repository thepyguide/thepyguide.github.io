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
