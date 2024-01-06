# 6.3. `pass` statement
The `pass` statement is used to do, well, nothing. Yes you heard that right,
`pass` statement does nothing! You might say it's useless then but it has 
various uses.

## In error handling
In `except` or other blocks, `pass` is used to do nothing. Lets say, we've
an error handling code that handles an error and simply ignores it, we can
use `pass` there.

```py
try:
    # do something here
    ...
except Exception:
    # do nothing if error occurs
    pass
```

When Python sees a `pass`, it does nothing on that line and moves to the
next line.

## In functions & codeblocks
In functions, `pass` is used as placeholder for missing code. Sometimes,
you write a function definition and leave the body to be written for future.

`pass` acts as a placeholder to prevent an error from empty code since
empty code is not allowed in codeblocks (if, else, loops, functions etc.)

=== "Without pass"

    ```py
    # THIS CODE RAISES AN ERROR

    def func():

    func()
    ```

=== "With pass"

    ```py
    # THIS CODE DOES NOT RAISE AN ERROR

    def func():
        pass

    func()
    ```
