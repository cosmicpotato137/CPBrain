

``` python
"""

Question 2

Write a function to determine whether a given string is valid.

A string is valid if its parentheses are valid and balanced:

that is, every type of parenthesis (round, square, bracket)

must be closed by the corresponding close-parenthesis.

  

For example:

Killing roaches [pt2] ({how} i learned to love the pesticide)

is a balanced string

Hello (world]) is not balanced

"""

def are_parentheses_balanced(string):
    open_chars = ['[', '{', '(']
    close_chars = [']', '}', ')']
    stack = []

    for char in string:
      if char in open_chars:
        stack.append(char)

      if char in close_chars:
        if (len(stack) == 0):
          return False

        close = stack[-1]
        stack = stack[:-1]

        if (open_chars.index(close) != close_chars.index(char)):
          return False

    if len(stack) == 0:
      return True
    return False
    
print(are_parentheses_balanced("[asdf]"))

#Test Cases

assert are_parentheses_balanced("([({}[(abcdefg)]other chars)][nonparentheses]{})abc") == True

assert are_parentheses_balanced("([({}[(abcdefg]other chars)][nonparentheses]{})abc") == False

assert are_parentheses_balanced("[(})]") == False
```