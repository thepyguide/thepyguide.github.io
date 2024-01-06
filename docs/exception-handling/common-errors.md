# 6.4. Common Errors
Following is a list of some common errors that are encountered in Python.

??? "`AttributeError`"

    This is raised when an attribute cannot be set or accessed
    on a class or object.

    Detail of this is covered in later sections.

??? "`IndexError`"

    This is raised when a string or a sequence index is greater than
    the maximum allowed index.

    For example, if we have a string of five characters `'Hello'`, the
    maximum index is `4` (starting from `0`). If we index this string
    with an index larger than `4`, `IndexError` is raised.

    For more information, see [section 4.1. Indexing Strings](../string-operations/indexing-strings.md#the-indexerror-error)

??? "`KeyError`"

    This is raised when a key does not exist in a dictionary. This
    is covered in detail in later sections.

??? "`KeyboardInterrupt`"

    Raised when a program is terminated with the ++ctrl+c++ key. This
    error shouldn't be handled.

??? "`NameError`"

    Raised when a variable is used which was never defined.

    ```py
    print(a)
    ```

    This code raises NameError since `a` is not defined.

??? "`SyntaxError`"

    Raised when an invalid syntax is used. This error cannot be
    handled in most cases.

??? "`IndentationError`"

    Raised when there is an indentation error.

??? "`TabError`"

    Raised when there is inconsistent use of tabs and spaces
    in indentation.

??? "`TypeError`"

    Raised when operation performed is on invalid type. This
    occurs in many cases with most common one being:

    - Invalid parameters in functions (extra or missing argument)
    - Mathematical operation between types that don't support mathematical
      operations.
    - Argument passed to a function is of invalid type.


??? "`UnboundLocalError`"

    Raised when a variable is accessed before it is defined.

    Example:

    ```py
    print(a)
    a = 20
    ```

??? "`ValueError`"

    Raised when a function gets a value of correct type but the
    value is improper. For example, passing non-convertible string
    to `int()` function.


??? "`ZeroDivisionError`"

    Raised when division by zero is attempted.


There are many other errors that are raised in various situations
but all of them cannot be documented here. See [Python Documentation](https://docs.python.org/3/library/exceptions.html) for more information.
