# 2.4. Mathematical Operations
In programming, we do a lot of computation. This computation more often than not involves
mathematical calculations. In this section, we'll see some mathematical operations we
can perform in Python.

## Basic Arithmetic
Following are the operators for basic arithmetic operations:

- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)

For example:

=== "Code"

    ```py
    n1 = 8
    n2 = 4

    # 8 + 4
    print('Sum:', n1 + n2)

    # 8 - 2
    print('Difference:', n1 - n2)

    # 8 × 2
    print('Product:', n1 * n2)

    # 8 ÷ 2
    print('Division:', n1 / n2)
    ```

=== "Output"

    ```
    Sum: 12
    Difference: 4
    Product: 32
    Division: 2.0
    ```

## Other Operations
Other operations that are also used often are:

- ``**`` (Power)
- ``//`` (Integer division)
- ``%`` (Modulus i.e remainder of division)

=== "Code"

    ```py
    n1 = 5
    n2 = 2

    # 5 raised to power 2
    print('Power:', n1 ** n2)

    # Integer division (//) returns the integer part of
    # division result. For example, 5 / 2 results in 2.5
    # but 5 // 2 returns 2.
    print('Division:', n1 // n2)

    # Modulus (%) returns remainder of division 
    print('Remainder:', n1 % n2)
    ```

=== "Output"

    ```
    Sum: 12
    Difference: 4
    Product: 32
    Division: 2.0
    ```

!!! warning "Pitfall Alert"

    Mathematical operations can only be performed between two values of `int` or
    `float` types. If you have a numeric string, you must convert it to proper
    data type first otherwise an error will occur.

    ```py
    n1 = '20'
    n2 = '30'
    print(n1 * n2)  # Error!
    ```
