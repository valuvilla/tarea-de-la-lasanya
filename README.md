# tarea-de-la-lasanya
proyecto básico 

https://github.com/valuvilla/tarea-de-la-lasanya.git

ntroduction
Python is a dynamic and strongly typed object-oriented programming language. It employs both duck typing and gradual typing, via type hints. Programming across paradigms is fully supported -- but internally, everything in Python is an object.

Python puts a strong emphasis on code readability and (similar to Haskell) uses significant indentation for function, method, and class definitions. The Zen of Python (PEP 20) and What is Pythonic? lay out additional philosophies.

Objects are assigned to names via the assignment operator, =. Variables are written in snake_case, and constants usually in SCREAMING_SNAKE_CASE.

A name (variable or constant) is not itself typed, and can be attached or re-attached to different objects over its lifetime. For extended naming conventions and advice, see PEP 8.

>>> my_first_variable = 1
>>> my_first_variable = "Last one, I promise"
>>> print(my_first_variable)
...
"Last one, I promise"
Constants are typically defined on a module or global level, and although they can be changed, they are intended to be named only once.

Their SCREAMING_SNAKE_CASE is a message to other developers that the assignment should not be altered:

# All caps signal that this is intended as a constant.
MY_FIRST_CONSTANT = 16

# Re-assignment will be allowed by the compiler & interpreter,
# but this is VERY strongly discouraged.
# Please don't do: MY_FIRST_CONSTANT = "Some other value"
The keyword def begins a function definition. It must be followed by the function name and a parenthesized list of zero or more formal parameters. Parameters can be of several different varieties, and can even vary in length. The def line is terminated with a colon.

Statements for the body of the function begin on the line following def and must be indented in a block. There is no strict indentation amount (either space OR [tab] characters are acceptable), but indentation must be consistent for all indented statements.

Functions explicitly return a value or object via the return keyword.

# Function definition on first line.
def add_two_numbers(number_one, number_two):
  return number_one + number_two  # Returns the sum of the numbers, and is indented by 2 spaces.

>>> add_two_numbers(3, 4)
7
Functions that do not have an explicit return expression will return None.

# This function will return None.
def add_two_numbers(number_one, number_two):
  result = number_one + number_two

>>> print(add_two_numbers(5, 7))
None
Inconsistent indentation will raise an error:

# The return statement line does not match the first line indent.
>>> def add_three_numbers_misformatted(number_one, number_two, number_three):
...     result = number_one + number_two + number_three   # Indented by 4 spaces.
...    return result     #this was only indented by 3 spaces
  File "<stdin>", line 3
    return result
                ^
IndentationError: unindent does not match any outer indentation level
Functions are called using their name followed by (). The number of arguments passed in the parentheses must match the number of parameters in the original function definition unless default arguments have been used:

>>> def number_to_the_power_of(number_one, number_two):
        """Raise a number to an arbitrary power.
        
        :param number_one: int the base number.
        :param number_two: int the power to raise the base number to.
        :return: int - number raised to power of second number
        
        Takes number_one and raises it to the power of number_two, returning the result.
        """
        
        return number_one ** number_two
...

>>> number_to_the_power_of(3,3)
27
A mis-match between parameters and arguments will raise an error:

>>> number_to_the_power_of(4,)
...
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: number_to_the_power_of() missing 1 required positional argument: 'number_two'

Adding a default value for a parameter can defend against such errors:

>>> def number_to_the_power_of_default(number_one, number_two=2):
        """Raise a number to an arbitrary power.
        
        :param number_one: int the base number.
        :param number_two: int the power to raise the base number to.
        :return: int - number raised to power of second number
        
        Takes number_one and raises it to the power of number_two, returning the result.
        """

        return number_one ** number_two

...
>>> number_to_the_power_of_default(4)
16
Methods bound to class names are invoked via dot notation (.), as are functions, constants, or global names imported as part of a module.:


import string

# This is a constant provided by the *string* module.
>>> print(string.ascii_lowercase)
"abcdefghijklmnopqrstuvwxyz"

# This is a method call of the str *class*.
>>> start_text = "my silly sentence for examples."
>>> str.upper(start_text)
"MY SILLY SENTENCE FOR EXAMPLES."

# This is a method call of an *instance* of the str *class*.
>>> start_text.upper()
"MY SILLY SENTENCE FOR EXAMPLES."
Comments in Python start with a # that is not part of a string, and end at line termination. Unlike many other programming languages, Python does not support multi-line comment marks. Each line of a comment block must start with the # character.

Comments are ignored by the interpreter:

# This is a single line comment.

x = "foo"  # This is an in-line comment.

# This is a multi-line
# comment block over multiple lines --
# these should be used sparingly.
The first statement of a function body can optionally be a docstring, which concisely summarizes the function or object's purpose. Docstrings are read by automated documentation tools and are returned by calling .__doc__ on the function, method, or class name. They can also function as lightweight unit tests, which will be covered in a later exercise. They are recommended for programs of any size where documentation is needed, and their conventions are laid out in PEP257:

# An example on a user-defined function.
>>> def number_to_the_power_of(number_one, number_two):
        """Raise a number to an arbitrary power.
        
        :param number_one: int the base number.
        :param number_two: int the power to raise the base number to.
        :return: int - number raised to power of second number
        
        Takes number_one and raises it to the power of number_two, returning the result.
        """

        return number_one ** number_two
...

>>> print(number_to_the_power_of.__doc__)
Raise a number to an arbitrary power.

    :param number_one: int the base number.
    :param number_two: int the power to raise the base number to.
    :return: int - number raised to power of second number

    Takes number_one and raises it to the power of number_two, returning the result.

# __doc__() for the built-in type: str.
>>> print(str.__doc__)
str(object='') -> str
str(bytes_or_buffer[, encoding[, errors]]) -> str

Create a new string object from the given object. If encoding or
errors is specified, then the object must expose a data buffer
that will be decoded using the given encoding and error handler.
Otherwise, returns the result of object.__str__() (if defined)
or repr(object).
encoding defaults to sys.getdefaultencoding().
errors defaults to 'strict'.
Instructions
You're going to write some code to help you cook a gorgeous lasagna from your favorite cookbook.

You have five tasks, all related to cooking your recipe.

Task 1
Define expected bake time in minutes

Define an EXPECTED_BAKE_TIME constant that returns how many minutes the lasagna should bake in the oven. According to your cookbook, the Lasagna should be in the oven for 40 minutes:

>>> import lasagna
>>> lasagna.EXPECTED_BAKE_TIME
40

Stuck? Reveal Hints
Opens in a modal
Task 2
Calculate remaining bake time in minutes

Task 3
Calculate preparation time in minutes

Task 4
Calculate total elapsed cooking time (prep + bake) in minutes

Task 5
Update the recipe with notes
