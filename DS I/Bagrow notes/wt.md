## Notes for A Whirlwind Tour of Python


<details>
<summary> View local variables in IPython </summary>

```python
%whos
```
</details>
</br>


<details>
<summary> View local variables otherwise </summary>

```python
locals() # returns a dict
for k,v in locals().items():
    print(k, '=', v)
```
</details>
</br>


<details>
<summary>What are the two methods for writing multiline code</summary>

You can use `()` or `\` however `()` are preferred.
```python
x = 1 + 2 + 3 +\
    4 + 5 + 6

x = (1 + 2 + 3
    +4 + 5 + 6)
```
</details>
</br>


<details>
<summary> 

```python
# Variables are pointers part 1:
# What is i equal to?

i = 5
j = i
j = 10
print(i)
```
</summary>

```python
i = 5       # Create int(5) instance, bind it to i
j = i       # bind j to the same int as i
j = 10      # Create int(3) instance, bind it to j
print(i)
>>> 5       # i is still bound to int(5), j is bound to int(3)
```
</details>
</br>


<details>
<summary> 

```python
# Variables as pointers part 2:
# What is j equal to?
i = [1,2,3]
j = i
i[0] = 5
print(j)
```
</summary>

```python
i = [1,2,3]     # Create list instance, bind it to i
j = i           # bind j to the same list as i
i[0] = 5        # Change first item of i
print(j)
>>> [5,2,3]     # j is still bound to same list as i
```
</details>
</br>


<details>
<summary>

```python
# Variables as pointers part 3:
# What is output
i = [1,2,3]
j = i
print(j)

i.append(4)
print(j)

i = "Hello!"
print(j)
```
</summary>

```python
i = [1,2,3]     # Create a list instance, bind i to it
j = i           # Bind j to the same list as i
print(j)        
>>> [1,2,3]     # j is still bound to same list as i

i.append(4)     # Add item to i
print(j)
>>> [1,2,3,4]   # j is still bound to same list as i

i = "Hello!"    # Create a string instance, bind i to it
print(j)
>>> [1,2,3,4]   # j is still bound to the list
```
</details>
</br>

When it comes to variables as pointers, think of it like this. If
```python
x = [1,2,3]
y = x
```

`y` is just using `x` to help identify the list `[1,2,3]`. `x` and `y` are only equal in the sense that they both point to the same list. However, if we reassign `x = "Hello!"` now `x` is pointing to a string instance while `y` is still pointing to a list. Hopefully that helps, and isn't too confusing.

- `x=[1,2,3]`: Assign `x` to the list `[1,2,3]`. 
- `y=x`: Find what x is pointing to and point y to the same object. At this point `x` and `y` are both pointing towards `[1,2,3]` but `y` is not going 'throught' `x` to get there. It only used `x` to help identify what object to point to.


<details>
<summary>
How can you check what class a variable is (int, float, set,...)
</summary>

```python
x = 5
type(x)
```
</details>
</br>


<details>
<summary>
How are types linked to variable names?
</summary>
They're not! Types are linked to the objects themselves.
</details>
</br>


<details>
<summary>
What is an object in Python
</summary>
An object is an entity that contains data and associated metadata and/or functionality.
</details>
</br>


<details>
<summary>
Metadata is also known as...
</summary>
Attributes
</details>
</br>


<details>
<summary>
The associated functionality for objects are also known as...
</summary>
Methods
</details>
</br>


<details>
<summary>
How do you access an objects various attributes and methods?
</summary>
With the dot syntax
</details>
</br>


Even simple objects like numerical types have real and imaginary attributes.
```python
x = 4.5
f"{x.real} + {x.imag}i"

>>> 4.5 + 0.0i
```
</br>


<details>
<summary>
How are methods and attributes different?
</summary>
Methods are like attributes except they are called using an opening and closing parenthesis
</details>
</br>


<details>
<summary>
Are methods and attributes objects?
</summary>
Yes! Everything in python is an object!

```python
type(x.is_integer())

>>> builtin_function_or_method
```
</details>
</br>


<details>
<summary>
List how to do the following operations

- Addition
- Subtraction
- Multiplication
- True division
- Floor division
- Modulus
- Exponentiation
- Negation
- Unary plus (rarely used)
</summary>

```python
a + b
a - b
a * b
a / b
a // b
a % b
a ** b
-a
+a
```
</details>
</br>


<details>
<summary>
What is a

```python
a = 24
a + 2
print(a)
```
</summary>

```python
>>> 24
```
</details>
</br>


<details>
<summary>
What are some examples of an augmented assignment operators?
</summary>

```python
a += b
a +- b
a +* b
...
```
</details>
</br>


<details>
<summary>
How are augmented assignment operators different for mutable objects like lists, arrays, or DataFrames?
</summary>
They modify the contents of the original object rather than creating a new object to store the result.
</details>
</br>

<details>
<summary>
How do you perform the following boolean comparisons?

- a equals b
- a less than b
- a less than or equal to b
- a not equal to b
- a greater than b
- a greater than or equal to b
</summary>

```python
a == b
a < b
a <= b
a != b
a > b
a >= b
```
</details>
</br>


<details>
<summary>
Identity and membership operators

- True if a and b are identical objects
- True if a and b are not identical objects
- True if a is a member of b
- True if a is not a member of b
</summary>

```python
a is b
a is not b
a in b
a not in b
```
</details>
</br>


<details>
<summary>
Please answer the following

```python
a = [1,2,3]
b = [1,2,3]
a == b
a is b
a is not b
```
</summary>

```python
a == b
>>> True
a is b
>>> False
a is not b
>>> True
```
</details>
</br>

<details>
<summary>

```python
a = [1,2,3]
b = a
a is b
```
</summary>

```python
True
```
</details>
</br>

This harkons back to what we were reviewing earlier. In the first part `a` and `b` point to different objects, while in the second they point to the same object.