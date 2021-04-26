# Ethical Hacker's Manual

This manual provides intel on the computer language the dark hackers are using to break into our system and steal info.

The dark hackers are using a **procedural** language. A procedural language breaks a large task into smaller subtasks (simple steps). The simple tasks are made up of different code blocks. This manual provides a description of different code blocks that hackers can use.  **RECOMMENDATION FROM HAYDEN: give a concrete example to help students understand, e.g. a recipe.**

## Variables
**RECOMMENDATION FROM HAYDEN: reduce type of variables to two: integer and boolean.**
The hackers use variables to store values. We try to give variables meaningful names that tell us what the variable is for. There are four kinds of variables: decimal, integer, character and boolean. Decimal values can be fractional: they have a decimal point (e.g., 3.5, 2.1, 5.0). Integer values are whole numbers (e.g., 2, 4, 6). Character values are letters or strings which we put in quotes (e.g., 'a', 'cat', 'My name is '). Boolean is a special kind of variable that has only two values: `true` or `false`. These values are generally also seen as `1` or `0`, respectively. **SUGGESTION BY HAYDEN: maybe relate to algebraic variables, e.g. y = x+5. y is an independent variable and x is the dependent variable.**

## Assignment
Assignment blocks consist of setting a variable to a value (number or string). We can also set variables equal to other previously set variables.

> EXAMPLE:

`x = 5` -> Sets the variable named "x" equal to 5

`y = 10` -> Sets the variable named "y" equal to 10

The variable names `x`, `y`, and `z` are good for the example, but if we were keeping track of the cost of items in our shopping basket, we might use:

`apples = 5`

`oranges = 10`

Boolean values are a results of comparisons done using comparison or logical operators (See Operators below).

> EXAMPLE:
`this_is_true = 10 > 4` -> this_is_true equals `true` or `1`.
`not_true = 10 < 4` -> not_true equals `false` or `0`.

## Operators
Operators make assignment useful. There are three types: mathematical, comparisons and logical. 

### Mathematical Operators
These are just like in math class: `+`, `-`, `*` and `/`. We can use these operators with values, variables or a combination of both. We can also use `+` with strings, e.g., `myName = 'Laura' + ' Smith'`. The `+` joins (concatenates) the two strings into one, so `myName` equals "Laura Smith" after assignment.

> EXAMPLE:

`z = 3 + 4` -> Sets "z" equal to 7. 
`z = 3.0 + 4.0` -> Sets "z" equal to 7.0.
`z = x + y`

> Question: If `x` and `y` are defined as in the example under "Assignment": what does z equal in the last example?

### Logical Operators
Logical operators let you test conditions. 
## `if` statements

`if` statements are also called conditional statements. They allow us to conditionally run code `if` the condition is true (or false)!

> EXAMPLE:

```matlab
if (x==5)
```

## **`for`** loops

If we need to do a task a specific number of times, we can use a `for` loop. We assign a variable that keeps track of how many times we want to repeat the task. We set this variable and the code inside the `for` loop is repeated as many times as we want.

> EXAMPLE:
We want to print out the numbers 1-5 to our computer display.  

```matlab
for i = 1:5
    print(i)
end % i is incremented at the end of the loop each time.
```
The output for this for loop is:

`1` 

`2` 

`3` 

`4` 

`5`


> Question: what would the output be if you replaced `print(i)` with `print('Hello!')` in the `for` loop example above?

##  Functions
All programming languages provide functions that perform specific tasks. They generally have the following parts:
* function name
* output variable name (some functions provide output, if so they will have an output variable or variables)
* input variable names (most functions will take input and process it in some way)

> EXAMPLE

```matlab
function output = myFunctionName(input1, input2)
    output = input1 + input2
end
```

