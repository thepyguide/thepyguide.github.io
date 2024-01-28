# 5.2. Arguments
In [section 5.1. Basics of Functions](./functions-basics.md), we learned about functions. This
section will cover function arguments.

As discussed in previous section, a function could take one or more arguments. An argument is
essentially an input to a function that it uses while processing to generate the output.

=== "Code"

    ```py
    def greet():
        print('From greet() function:')
        print('Hello, World!')

    def greet_with_name(name):
        print('From greet_with_name() function:')
        print(f'Hello, {name}!')

    greet()
    greet_with_name('John')
    ```

=== "Output"

    ```
    From greet() function:
    Hello, World!
    From greet_with_name() function:
    Hello, John!
    ```

In above code, there are two functions. `greet` function does not take any arguments while
`greet_with_name` takes one argument: `name`.

!!! note "Parameter vs Argument"

    The terms "parameter" and "argument" are often used synonymously and have the
    same meaning in general but technically speaking:

    - A parameter is the variable used when defining the function.
    - An argument is the value/variable passed to the function while calling it.

    ```py linenums="1"
    def add(n1, n2):
        return n1 + n2

    result = add(5, 2)
    print(result)
    ```

    In this case, `n1` and `n2` on line 1 are parameters and `5` and `2` on line 4 are
    arguments. It is normal to use these terms interchangably.

## Default Arguments
Normally, when we don't pass an argument when calling a function that expects arguments, we
get an error:

=== "Code"

    ```py
    def greet(name):
        print(f'Hello, {name}!')

    greet()
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "C:\XGuides\python\test.py", line 4, in <module>
        greet()
    TypeError: greet() missing 1 required positional argument: 'name'
    ```

We can assign default values to arguments that are used when no value for that argument
is passed upon calling it.

=== "Code"

    ```py
    def greet(name='World'):
        print(f'Hello, {name}!')

    greet()
    greet('John')
    ```

=== "Output"

    ```
    Hello, World!
    Hello, John!
    ```

In code shown, the first call doesn't provide any argument so it uses the default value. In
second call, a value is passed which is used instead of default.

!!! warning "Position of default arguments"

    Default arguments should must be placed *after* required arguments in a function
    that has both default and required arguments.

    **WRONG:**
    === "Code"

        ```py
        def func(optional='', required):
            ...
        ```

    === "Error"

        ```
        File "C:\XGuides\python\test.py", line 1
          def func(optional='', required):
                                ^^^^^^^^
        SyntaxError: non-default argument follows default argument
        ```

    **CORRECT:**
    ```py
    def func(required, optional=''):
        ...
    ```

    This is only the case for positional arguments. Keyword arguments don't have
    this caveat.

## Positional & Keyword Arguments
Consider the following code:

=== "Code"

    ```py
    def greet(name, informal):
        if informal:
            print(f'Howdy, {name}!')
        else:
            print(f'Hello, {name}!')

    greet('John', True)
    ```

=== "Output"

    ```
    Howdy, John!
    ```

In this code, when calling the function, the parameters are passed in the same sequence as they
are defined. These are called "positional arguments".

On the other hand, the function could also be called like this:

=== "Code"

    ```py
    greet('John', informal=True)
    ```

=== "Output"

    ```
    Howdy, John!
    ```

In this case, `'John'` (the value for `name`) is the positional argument and `informal=True`
is a "keyword argument".

Alternatively, both arguments could be passed as keyword arguments:

=== "Code"

    ```py
    greet(name='John', informal=True)
    ```

=== "Output"

    ```
    Howdy, John!
    ```

- Keyword arguments are arguments that are passed by explicitly assigning the value to the
  argument using its name.

- Positional arguments are arguments that are passed as per the sequence of arguments defined
  in function header.

!!! warning

    Keyword arguments should be passed *after* positional arguments.

## Variadic Arguments
Until now, we defined functions that either took no argument or a specific number of arguments.
We can also define functions that can take variable amount of arguments.

### Variadic Positional Arguments
=== "Code"

    ```py
    def greet(*names):
        for name in names:
            print(f'Hello, {name}!')

    greet('John', 'Peter', 'Alex')
    ```

=== "Output"

    ```
    Hello, John!
    Hello, Peter!
    Hello, Alex!
    ```

In this code, `*names` in arguments list means that this argument can take variable amount
of arguments. Inside the function, `names` is a [tuple](../data-structures/tuples/introduction.md) of values that were passed.

=== "Code"

    ```py
    def greet(*names):
        print(names[0])
        print(names[1])
        print(names[2])

    greet('John', 'Peter', 'Alex', 'Marsh')
    ```

=== "Output"

    ```
    John
    Peter
    Alex
    ```

### Variadic Keyword Arguments
We can also take variable keyword arguments by adding double `*` before the argument name.

=== "Code"

    ```py
    def func(**args):
        print(args['arg1'])
        print(args['arg2'])

    func(arg1='hello', arg2='world', arg3='bye', arg4='world')
    ```

=== "Output"

    ```
    hello
    world
    ```

<!-- TODO: Ref Dictionaries -->
In function body, variadic keyword arguments are treated as a dictionary with key
representing the name of argument and value representing the passed value.

### Mixing Arguments
Positional and keyword arguments can also be mixed in same function.

=== "Code"

    ```py
    def func(*args, **kwargs):
        print(args[0])
        print(args[1])
        print(kwargs['arg1'])
        print(kwargs['arg2'])

    func('hello', 'world', 'test', arg1='hello world', arg2='bye world')
    ```

=== "Output"

    ```
    hello
    world
    hello world
    bye world
    ```

**Note that positional arguments are always put before keyword arguments otherwise
an error is raised.**

If there is a function that takes variadic positional arguments and normal positional
arguments as well, the normal arguments would have to be passed as keyword arguments.

=== "Code"

    ```py
    def func(*args, normal_arg, normal_arg2):
        print(normal_arg)
        print(normal_arg2)

    # Normal arguments (non-variadic arguments) have to be passed
    # as keyword arguments.
    func('hello', 'world', 'test', normal_arg='hello world', normal_arg2='bye world')
    ```

=== "Output"

    ```
    hello world
    bye world
    ```

## Positional-only Arguments
Sometimes you want some arguments to only be passed as positional instead of keyword. You
can do this by adding a `/` after the arguments that are to be passed as positional.

```py
def func(pos_only, pos_only2, /, other, other2):
    ...  # function body here
```

The arguments before `/` symbol cannot be passed as keyword arguments and the
ones after `/` can be passed as keyword or positional.

```py
func(1, 2, 3, 4)  # no error
func(1, 2, 3, other2=4)  # no error
func(pos_only=1, pos_only2=2, other=3, other2=4)  # ERROR
```

On third line, there is an error since first two arguments have to be positional.

## Keyword-only Arguments
Similar to positional-only arguments, arguments can also be marked as keyword-only
using `*` symbol.
```py
def func(arg1, arg2, *, kwarg1, kwarg2):
    ...  # function body here
```

The arguments after `*` symbol cannot be passed as positional arguments and the
ones before `*` can be passed as keyword or positional.

```py
func(1, 2, kwarg1=3, kwarg2=4)  # no error
func(arg1=1, arg2=2, kwarg1=2, kwarg2=3)  # no error
func(1, 2, 3, kwarg2=4)  # ERROR
func(1, 2, 3, 4)  # ERROR
```

- On third call, `3` (value for `kwarg1`) must be passed as keyword argument.
- On fourth call, both `3` and `4` have to be passed as keyword arguments.

---

!!! tip

    Positional-only and Keyword-only arguments can also be mixed in same function.

    ```py
    def func(arg1, arg2, /, arg3, arg4, *, arg5, arg6):
        pass
    ```

    - `arg1` and `arg2` are positional only.
    - `arg3` and `arg4` can either be passed as positional or keyword.
    - `arg5` and `arg6` are keyword only.
