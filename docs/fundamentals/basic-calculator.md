# 2.6. Writing a basic calculator
Now that we have learnt about mathematical operations and I/O operations, we'll be using
our current knowledge to write a very simple calculator program that will simply add two
numbers.

!!! info

    As we progress in this guide and learn new things in Python, we'll be applying our
    knowledge on this calculator to improve it and add more features to it.

Our calculator will be doing the following things:

1. Take two numbers from user.
2. Adding the numbers together.
3. Showing the result of calculation to the user.

## Taking the input
=== "Code"

    ```py linenums="1"
    print('Welcome to my calculator')
    print()  # gap of one line before input prompt

    n1 = int(input('Enter the first number: '))
    n2 = int(input('Enter the second number: '))
    ```

=== "Output"

    ```
    Welcome to my calculator

    Enter the first number: 20
    Enter the second number: 30
    ```

Here, we're showing user a simply message to greet them in the program. A `print()` statement
without any message arguments simply prints a newline. We're using that to add a gap between
the input prompts and the greeting message.

We're then taking two numbers as input. Since we want to perform mathematical operations on
the input, we're also converting it to the `int` data type as we learned in previous sections.

If you run the program and look at the output, the program currently only asks for two numbers
to be input but doesn't show any result after input.

## Processing and Output
Now we'll add the following line of codes to our previous code.
```py linenums="1" hl_lines="7 8 9"
print('Welcome to my calculator')
print()  # gap of one line before input prompt

n1 = int(input('Enter the first number: '))
n2 = int(input('Enter the second number: '))

result = n1 + n2
print()
print('Result:', result)
```

We're simply adding the two numbers, storing the result of sum in a variable `result`. Again,
using the `print()` function without any parameters gives a newline which we use to add a
gap between input prompts and result.

... and with that being said, our calculator is now ready to go. Run the program and give
it the two numbers and you'll see the result.

Output:
```
Welcome to my calculator

Enter the first number: 20
Enter the second number: 30

Result: 50
```
As we learn more features, we'll come back to this small project and improve it by adding
new features so keep this calculator program saved.
