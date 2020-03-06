Title: List comprehensions
Date: 2019-11-02
Category: Blog
Status: draft
 
Understanding and being able to use comprehensions in Python is great fun and will speed up your problem solving. They are not a replacement for the standard for loop - they solve the simpler needs well.
 
 
### [function(item) for item in iterable if condition]
 
 Compared to a standard for loop, a list comprehension is a quick way to process the elements of a list with the ability to filter and modify.
 
```python
l = [2 * n for n in (0, 1, 2) if n > 0]
l
>> [2, 4]
```

The list (actually this is a tuple, but it can be any iterable object) is the number 0, 1, 2. The function is multiplying n by 2 and the condition is greater than 0.

So the output is 1 * 2 and 2 * 2 because the first item doesn't pass the filter (condition)

A common task where I use list comprehensions is to tidy up column names in Pandas.

```python
df.columns = [c.replace(' ','').lower() for c in df.columns]
```

This replaces spaces with underscore and makes all letters lowercase. Notice I don't have to use the filter ability - I can leave it out if I want to process every item of the iterable object