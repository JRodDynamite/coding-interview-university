## Problem

[Problem Link](https://www.codewars.com/kata/526571aae218b8ee490006f4/train/python)

Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that input is non-negative.

Example: The binary representation of 1234 is 10011010010, so the function should return 5 in this case

## Initial Solution:

```python
def count_bits(n):
    for i in range(1000):
        if 2**i >= n:
            nob = i+1
            break
    onebit = 0
    for i in reversed(range(nob)):
        if 2**i <= n:
            onebit+=1
            n-=(2**i)
        if n == 0:
            break    
    return onebit
```

 - Without bitwise operators.
 - Could be more optimized.

## Best Solution

```python
def count_bits(n):
    onebit = 0
    while(n):
        if n & 1 == 1:
            onebit += 1
        n >>= 1
    return onebit
```

 - With bitwise operators
 - Only loop that can max go upto max num of bits

## Learnings
 - Make use of [bitwise operators](https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/)
   - The **& (bitwise AND)** in C or C++ takes two numbers as operands and does AND on every bit of two numbers. The result of AND is 1 only if both bits are 1.
   - The **| (bitwise OR)** in C or C++ takes two numbers as operands and does OR on every bit of two numbers. The result of OR is 1 if any of the two bits is 1.
   - The **^ (bitwise XOR)** in C or C++ takes two numbers as operands and does XOR on every bit of two numbers. The result of XOR is 1 if the two bits are different.
   - The **<< (left shift)** in C or C++ takes two numbers, left shifts the bits of the first operand, the second operand decides the number of places to shift.
   - The **>> (right shift)** in C or C++ takes two numbers, right shifts the bits of the first operand, the second operand decides the number of places to shift.
   - The **~ (bitwise NOT)** in C or C++ takes one number and inverts all bits of it.