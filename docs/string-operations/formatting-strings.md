# 4.3. Formatting Strings
In this section, we'll discuss some ways of formatting strings.

## Concatenating strings
Two strings can be added to produce a new joined string.

=== "Code"

    ```py
    string1 = 'Hello'
    string2 = 'World'
    print(string1 + ' ' + string2)
    ```

=== "Output"

    ```
    Hello World
    ```

Note that a string can only be added to a string. If we add another data type to a string,
an error is raised:

=== "Code"

    ```py
    to_add = 1
    print('Hello' + to_add)
    ```

=== "Output"

    ```
    Traceback (most recent call last):
      File "G:\thepyguide\main.py", line 2, in <module>
        print('Hello' + to_add)
            ~~~~~~~~^~~
    TypeError: can only concatenate str (not "int") to str
    ```

<!-- -->

The right way of doing this is to convert the value to be added to string before addition:

=== "Code"

    ```py
    to_add = 1
    print('Hello' + str(to_add))
    ```

=== "Output"

    ```
    Hello1
    ```

## The `format()` method
The `format()` method is used to format a string and include variable values to it.

=== "Code"

    ```py
    name = input('Enter your name: ')
    nickname = input('Enter your nickname: ')

    greeting = 'Hello, {}. I will call you {} from now'.format(name, nickname)
    print(greeting)
    ```

=== "Output"

    ```
    Enter your name: John
    Enter your nickname: Jay
    Hello, John. I will call you Jay from now
    ```

`{}` placeholder is replaced with the arguments provided to `format()` method. Note the order
is important. The first argument is substituted with first `{}` in the string and
vice versa.

### Changing placeholders order
To change the order, the indexes can be used:

=== "Code"

    ```py
    name = input('Enter your name: ')
    nickname = input('Enter your nickname: ')

    greeting = 'Hello, {1}. I will call you {0} from now'.format(name, nickname)
    print(greeting)
    ```

=== "Output"

    ```
    Enter your name: John
    Enter your nickname: Jay
    Hello, Jay. I will call you John from now
    ```

Here, `{1}` is replaced with second argument and `{0}` is replaced with first argument.

### Different data types
Unlike concatenating strings, the arguments in `format()` are automatically converted
to string and don't have to be of `str` data type.

=== "Code"

    ```py
    n1 = int(input('Enter first number: '))
    n2 = int(input('Enter second number: '))
    product = n1 * n2

    print('The product is: {}'.format(product))
    ```

=== "Output"

    ```
    Enter first number: 20
    Enter second number: 3
    The product is 60.
    ```

### Named placeholders
The curly brackets could include an identifier name which would be used while formatting
the string.

=== "Code"

    ```py
    template = 'Hello, {real_name}. I will call you {nick} from now'
    name = input('Enter your name: ')
    nickname = input('Enter your nickname: ')
    print(template.format(real_name=name, nick=nickname))
    ```

=== "Output"

    ```
    Hello, John. I will call you Jay from now.
    ```

## f-string
f-string is a more convenient method of formatting. It is clearer and more readable than
the `format()` method.

To use an f-string, `f` is placed before the opening quote of a string and variables
or values to include in strings are put in curly brackets.

=== "Code"

    ```py
    name = input('Enter your name: ')
    nickname = input('Enter your nickname: ')

    greeting = f'Hello, {name}. I will call you {nickname} from now'
    print(greeting)
    ```

=== "Output"

    ```
    Enter your name: John
    Enter your nickname: Jay
    Hello, John. I will call you Jay from now
    ```

Similar to format, the values inside curly brackets could be of any data type and would
automatically be converted to string.

Expressions could also be used:

=== "Code"

    ```py
    n1 = int(input('Enter first number: '))
    n2 = int(input('Enter second number: '))

    print(f'The product is: {n1 * n2}')
    ```

=== "Output"

    ```
    Enter first number: 20
    Enter second number: 3
    The product is 60.
    ```
