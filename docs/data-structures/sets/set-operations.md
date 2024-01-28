# 7.3.3. Set Operations
Sets are generally used for operations similar to mathematical
sets like union, intersection, and difference, etc.

## Union
Union of two sets `x` and `y` produces a new set with elements
of both `x` and `y`.

For this, we can either use the `|` operator.

=== "Code"

    ```py
    x = {'a', 'b', 'c'}
    y = {'c', 'd', 'e', 'f'}
    z = x | y
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b', 'c', 'd', 'e', 'f'}
    ```

or we can use the `set.union()` method:

=== "Code"

    ```py
    x = {'a', 'b', 'c'}
    y = {'c', 'd', 'e', 'f'}
    z = x.union(y)
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b', 'c', 'd', 'e', 'f'}
    ```

As seen here, union combines the two sets. Note that since sets
don't allow duplicates, the `"c"` which was in both sets appears
only once.

!!! tip "`|` vs `set.union()`"

    `|` and `set.union()` operates the same way except one
    caveat: we can pass any sequence in `set.union()` like
    list or tuple which isn't the case for `|` operator.

We also have `set.update()` which instead of creating new
set, updates the original set.

=== "Code"

    ```py
    x = {'a', 'b', 'c'}
    y = {'c', 'd', 'e', 'f'}
    x.update(y)
    print(x)
    ```

=== "Output"

    ```
    {'a', 'b', 'c', 'd', 'e', 'f'}
    ```

## Intersection
Intersection of two sets `x` and `y` produces a new set with
elements that are common in both `x` and `y`.

`&` operator is used for intersection of two sets:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x & y
    print(z)
    ```

=== "Output"

    ```
    {'c', 'd'}
    ```

Alternatively, set provides a `set.intersection()` method:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x.intersection(y)
    print(z)
    ```

=== "Output"

    ```
    {'c', 'd'}
    ```

!!! tip "`&` vs `set.intersection()`"

    `|` and `set.intersection()` do the same thing but
    `set.intersection()` allows other sequences to be
    passed such as list or tuple.

Similar to `set.update()`, we can use `set.intersection_update()`
that updates the original set instead of creating a new one.

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    x.intersection_update(y)
    print(x)
    ```

=== "Output"

    ```
    {'c', 'd'}
    ```

## Difference
Difference of sets `x` and `y` returns a new set with
elements that are present in `x` but not in `y`.

`-` operator is used for finding difference between two sets:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x - y
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b'}
    ```

Set also provides a `set.difference()` method:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x.difference(y)
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b'}
    ```

!!! tip "`-` vs `set.difference()`"

    `-` and `set.difference()` both calculate the difference
    but `set.difference()` allows other sequences to be
    passed as parameter such as list or tuple.

Similar to previous operations, we can use `set.difference_update()`
that updates the original set instead of creating a new one.

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    x.difference_update(y)
    print(x)
    ```

=== "Output"

    ```
    {'a', 'b'}
    ```

## Symmetric Difference
Symmetric difference of sets `x` and `y` returns a new set with all
elements that are present in either `x` or `y` but not both.

In simpler words, elements that are in both sets are excluded
in new set.

`^` operator is used for finding symmetric difference between
two sets:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x ^ y
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b', 'e', 'f'}
    ```

Set also provides a `set.symmetric_difference()` method:

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    z = x.symmetric_difference(y)
    print(z)
    ```

=== "Output"

    ```
    {'a', 'b', 'e', 'f'}
    ```

!!! tip "`^` vs `set.symmetric_difference()`"

    `^` and `set.symmetric_difference()` both calculate the
    difference but `set.symmetric_difference()` allows other
    sequences to be passed as parameter such as list or tuple.

Similar to previous operations, we can use `set.symmetric_difference_update()` that updates the original set
instead of creating a new one.

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'c', 'd', 'e', 'f'}
    x.symmetric_difference_update(y)
    print(x)
    ```

=== "Output"

    ```
    {'a', 'b', 'e', 'f'}
    ```

## Disjoint
`x` and `y` are disjoint sets if they have no elements in common.

This is checked using the `set.isdisjoint()` method. `x.isdisjoint(y)`
returns True if `x` and `y` have no elements in common:

=== "Code"

    ```py
    x = {'a', 'b', 'c'}
    y = {'d', 'e', 'f'}
    print(x.isdisjoint(y))
    ```

=== "Output"

    ```
    True
    ```

!!! note

    There is no operator available for `set.disjoint()`.

## Subset
`x` is a subset of `y` if `y` contains all elements of `x`.

`x.issubset(y)` returns `True` if `x` is a subset of `y`.

=== "Code"

    ```py
    x = {'a', 'b', 'c'}
    y = {'a', 'b', 'c', 'd', 'e'}
    print(x.issubset(y))
    ```

=== "Output"

    ```
    True
    ```

`<=` operator can also be used for checking subset.
`x <= y` is equivalent to `x.issubset(y)`.

!!! tip "`<=` vs `set.issubset()`"

    `<=` and `set.issubset()` both are same in terms of
    behaviour with `set.issubset()` also allowing other sequences
    to be passed such as list or tuple.

!!! tip "Proper Subset"

    X is a proper subset of Y if X contains all elements of Y
    and X and Y are not equal sets.

    To report proper subsets, `x < y` operation is used.

    ```py
    x = {'a', 'b', 'c'}
    y = {'a', 'b', 'c', 'd'}
    z = {'a', 'b', 'c'}

    print(x <= y)  # True (x is a subset of y)
    print(x < y)  # True (x is a proper subset of y)
    print(x <= z)  # True (x is a subset of z)
    print(x < z)  # False (x is not a proper subset of z)
    ```

    There is no specific method for reporting proper subset.

## Superset
`x` is a superset of `y` if `x` contains all elements of `y`.

`x.issuperset(y)` returns `True` if `x` is a superset of `y`.

=== "Code"

    ```py
    x = {'a', 'b', 'c', 'd', 'e'}
    y = {'a', 'b', 'c'}
    print(x.issuperset(y))
    ```

=== "Output"

    ```
    True
    ```

For this method, `>=` operator is used. `x >= y` is equivalent
to `x.issuperset(y)`.

!!! tip "`>=` vs `set.issuperset()`"

    `>=` and `set.issuperset()` both are same in terms of
    behaviour with `set.issuperset()` also allowing other sequences
    to be passed such as list or tuple.

!!! tip "Proper Superset"

    X is a proper superset of Y if X contains all elements of Y
    and X and Y are not equal.

    `x > y` operation can be used to check for proper superset.

    ```py
    x = {'a', 'b', 'c', 'd'}
    y = {'a', 'b', 'c'}
    z = {'a', 'b', 'c', 'd'}

    print(x >= y)  # True (x is a superset of y)
    print(x > y)  # True (x is a proper subset of y)
    print(x >= z)  # True (x is a subset of z)
    print(x > z)  # False (x is not a proper subset of z)
    ```

    There is no specific method for reporting proper superset.

---

!!! tip "Learn about sets"

    To understand the operations shown more thoroughly, consider
    checking out the following pages:

    - [Wikipedia: Set Basic Operations](https://en.wikipedia.org/wiki/Set_(mathematics)#Basic_operations)
    - [Wikipedia: Subset & Superset](https://en.wikipedia.org/wiki/Subset)
