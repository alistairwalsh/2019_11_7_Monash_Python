1. Write a program that repeatedly prompts a user for integer numbers until the user enters 'done'. 

2. Once 'done' is entered, print out the largest and smallest of the numbers. 

3. If the user enters anything other than a valid number catch it with a try/except and put out an appropriate message and ignore the number. 

4. Enter 7, 2, bob, 10, and 4 and match the output below.


```python
largest = None
smallest = None
while True:
    num = input("Enter a number: ")
    if num == "done" : break
    print(num)

print("Maximum", largest)
```

Desired output

> Invalid input

> Maximum is 10

> Minimum is 2