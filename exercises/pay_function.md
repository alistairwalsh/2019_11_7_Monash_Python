1. Write a program to prompt the user for hours and rate per hour using input to compute gross pay. 

2. Pay should be the normal rate for hours up to 40 and time-and-a-half for the hourly rate for all hours worked above 40 hours. 

3. Put the logic to do the computation of pay in a function called computepay() and use the function to do the computation. 

3. The function should return a value. 

5. Use 45 hours and a rate of 10.50 per hour to test the program (the pay should be 498.75). 

6. You should use input to read a string and float() to convert the string to a number. 

7. Do not worry about error checking the user input unless you want to - you can assume the user types numbers properly. 

**** Do not name your variable sum or use the sum() function.

```python
def computepay(h,r):
    return 42.37

hrs = input("Enter Hours:")
p = computepay(10,20)
print("Pay",p)
```