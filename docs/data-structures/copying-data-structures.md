# 7.6. Copying Data Structures
This section covers the difference between storing references and creating
copies of data structure.

## Reference vs Copy
If we have a data structure, for example a [list](./lists/introduction.md)
stored in a variable `x`:

```py
x = ['a', 'b', 'c']
```

... and we want to create a copy of this list and store it in another
variable, say `y`, what would be the way for doing that?

A naive solution to this problem would be as simple as:

=== "Code"

    ```py
    x = ['a', 'b', 'c']
    y = x
    print(y)
    ```

=== "Output"

    ```
    ['a', 'b', 'c']
    ```

That looks fine, so far. Though there is one huge problem, we want
to create a copy of `x` and store it into `y` such that `y` is an
independent list but with this approach, if we change `y`, `x` list
is also changed:

=== "Code"

    ```py
    x = ['a', 'b', 'c']
    y = x
    print('x before update:', x)
    print('y before update:', y)

    y.append('d')
    print('x after update:', x)
    print('y after update:', y)
    ```

=== "Output"

    ```
    x before update: ['a', 'b', 'c']
    y before update: ['a', 'b', 'c']
    x after update: ['a', 'b', 'c', 'd']
    y after update: ['a', 'b', 'c', 'd']
    ```

To understand what's happening here, when we assign `y = x`, we're
simply creating a new variable `y` that references `x`. `y` is not
a new list but merely a reference to `x`. This means whenever we
access `y`, we're in turn accessing `x` instead.

Same is the case for other data structures (except tuples because they
are immutable), and virtually any mutable type.

## Creating Copies
All data structures (except tuple) provide a `copy()` method that
can be used to create a copy of that data structure.

=== "Code"

    ```py
    x = ['a', 'b', 'c']
    y = x.copy()
    print(y)
    ```

=== "Output"

    ```
    ['a', 'b', 'c']
    ```

Now, `y` is a copy of `x` instead of a reference to it. Hence, now modifying
`y` would only change the new list we created instead of changing the 
original list stored in `x`:

=== "Code"

    ```py
    x = ['a', 'b', 'c']
    y = x.copy()
    print('x before update:', x)
    print('y before update:', y)

    y.append('d')
    print('x after update:', x)
    print('y after update:', y)
    ```

=== "Output"

    ```
    x before update: ['a', 'b', 'c']
    y before update: ['a', 'b', 'c']
    x after update: ['a', 'b', 'c']
    y after update: ['a', 'b', 'c', 'd']
    ```

Note how `x` remains same both before and after the update.

## Shallow Copy vs Deep Copy
What we just did is called creating a "shallow copy." What is a shallow
copy you may ask, so let us have another example.

=== "Code"

    ```py
    x = ['a', 'b', 'c', [1, 2, 3]]
    y = x.copy()
    print('x before update:', x)
    print('y before update:', y)

    y.append('d')
    print('x after update:', x)
    print('y after update:', y)
    ```

=== "Output"

    ```
    x before update: ['a', 'b', 'c', [1, 2, 3]]
    y before update: ['a', 'b', 'c', [1, 2, 3]]
    x after update: ['a', 'b', 'c', [1, 2, 3]]
    y after update: ['a', 'b', 'c', [1, 2, 3], 'd']
    ```

In this case, `x` has list has another [nested list](./lists/introduction.md#nestable) `[1, 2, 3]`. We created a copy of `x` and stored it in `y`
and after that we modified `y`, adding a new element `"d"`.

So far so good. However, we'll notice the problem when we try to change
the nested list:

=== "Code"

    ```py
    x = ['a', 'b', 'c', [1, 2, 3]]
    y = x.copy()
    print('x before update:', x)
    print('y before update:', y)

    # y[3] is the nested list
    y[3].append(4)
    print('x after update:', x)
    print('y after update:', y)
    ```

=== "Output"

    ```
    x before update: ['a', 'b', 'c', [1, 2, 3]]
    y before update: ['a', 'b', 'c', [1, 2, 3]]
    x after update: ['a', 'b', 'c', [1, 2, 3, 4]]
    y after update: ['a', 'b', 'c', [1, 2, 3, 4]]
    ```

As you can see, when we update the nested list, it is updated in both
`x` and `y`. This might seem unexpected because we just established that
`x.copy()` creates a new copy of list which is independent of original
list. This is what we call "shallow copying".

**Shallow copying** only copies the data structure but not the elements
of that data structure.

To avoid this problem, we have **deep copying** that along with copying
the data structure, copies the elements stored in it too. In order to
use deep copying, we require an external module which will be covered in
a later section.
