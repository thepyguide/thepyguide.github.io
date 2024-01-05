# 5.4. Scopes
Scopes in Python determines the places in your code where a specific variable or
function is valid or can be accessed.

!!! note

    In this article, the term "name" is used to generally refer to anything a
    scope holds such as a variable or function.

## Global Scope
Global scope, also known as module scope, holds the names that are accessible throughout
the program.

=== "Code"

    ```py
    var = 42

    def show_var():
        print('accessing var from inside function:', var)

    print('accessing var from outside function:', var)
    show_var()
    ```

=== "Output"

    ```
    accessing var from outside function: 42
    accessing var from inside function: 42
    ```

Here, `var` is a variable defined in global scope, hence called "global variable".

Note that `show_var` function is also a global function. Another function could call
`show_var` function in its body without a problem since it is defined globally.

### `global` statement
You cannot update a variable defined in global scope from inside a function.

=== "Code"

    ```py
    var = 42

    def update_var():
        var = var + 1

    update_var()
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 6, in <module>
        update_var()
      File "C:\XGuides\python\test.py", line 4, in update_var
        var = var + 1
            ^^^
    UnboundLocalError: cannot access local variable 'var' where it is not associated with a value
    ```

To do so, we use the `global` statement.

=== "Code"

    ```py
    var = 42

    def update_var():
        global var
        var = var + 1

    update_var()
    print(var)  # 43
    update_var()
    print(var)  # 44
    ```

=== "Output"

    ```
    43
    44
    ```

When a variable is declared as `global`, its value can be manipulated globally from inside
a function or another scope.

!!! warning

    Using `global` is considered a bad practice because it tends to lead to problems
    in the long run. If you're using `global` in your code, look for alternative
    solutions as there's always a better approach to the problem.

    For example, one approach to write above code without global could be:

    ```py
    var = 42

    def update_var():
        var = var + 1

    var = update_var()
    print(var)  # 43
    var = update_var()
    print(var)  # 44
    ```

## Local Scope
Local scope is a scope created by a function. It holds names that are only valid
inside the function that the scope belongs to.

Names inside local scopes are only valid inside the function and cannot be used
outside it:

=== "Code"

    ```py
    def func():
        var = 42
        print('inside function:', var)

    func()
    print('outside function:', var)  # raises an error
    ```

=== "Output"

    ```
    inside function: 42
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 6, in <module>
        print('outside function:', var)  # raises an error
                                   ^^^
    NameError: name 'var' is not defined.
    ```

`var` is created in function's local scope when function is called and when function
is done executing, that scope is removed along with all the variables defined in it.

Note that arguments of a function are also part of local scope and can only be accessed
and manipulated within that function.

## Enclosing Scope
Enclosing scope comes into play when we have [nested functions](./return-value.md#returning-nested-functions) (function defined inside another function).

Consider the following example:
```py
def outer():
    var = 42

    def inner():
        print(var)
```

In this case, the enclosing scope of `inner` is local scope of `outer`.

### `nonlocal` statement
Names defined in enclosing scope such as `var` can be accessed by inner function
but cannot be updated.

=== "Code"

    ```py
    def outer():
        var = 42

        def inner():
            var = var + 1

        inner()

    outer()
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 9, in <module>
        outer()
      File "C:\XGuides\python\test.py", line 7, in outer
        inner()
      File "C:\XGuides\python\test.py", line 5, in inner
        var = var + 1
              ^^^
    UnboundLocalError: cannot access local variable 'var' where it is not associated with a value
    ```

To do this, we use the `nonlocal` statement.

=== "Code"

    ```py
    def outer():
        var = 42

        def inner():
            nonlocal var
            var = var + 1

        print('before inner called:', var)
        inner()
        print('after inner called:', var)

    outer()
    ```

=== "Output"

    ```
    before inner called: 42
    after inner called: 43
    ```
