# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)

#### Arrays & Strings

---

1. Write a function that takes in a list/ array of numbers and returns the maximum value in the array. Solve without any build in methods.

   - Steps:
     - Initialize the _max_number_ variable to the smallest number possible.
     - Itirate through the array checking if any element is greater than the current _max_number_.
     - Update the _max_number_ variable accordingly.
   - [Video Walkthrough](https://www.youtube.com/watch?v=fydPf6rO5-E)

```python
def max_value(nums):
 max_num = -float('inf')
 for n in nums:
   if n > max_num:
   max_num = n
 return max_num
```

---

2. Write a function that takes in a list/ array of numbers and returns an array with only the prime numbers from the original list/ array. If there are no primes, it returns an empty list.

   - Steps:
     - Create a helper function Initialize the _is_prime(n)_
       - This function returns _True_ if _n_ is prime and _False_ otherwise.
       - For efficiency, you could only iterate from $2 - \frac{n}{2}$ to find any multiples of n.
     - Use the _filter(func, seq) function to itiratively call \_is_prime(n)_ on the input list/ array.

   ```python
   def is_prime(n):
    if n < 2: return False
    for i in range (2, int(n**(1/2)) + 1):
      if n % i == 0: return False
    return True
   ```

   ```python
     prime_nums = list(filter(is_prime, nums))
   ```

---

3. Write a function that takes in a string as an argument and a Write a function that takes in a list/ array of numbers and returns an array with only the prime numbers from the original list/ array. If there are no primes, it returns an empty list.

   - Steps:
     - Create a helper function Initialize the _is_prime(n)_
       - This function returns _True_ if _n_ is prime and _False_ otherwise.
       - For efficiency, you could only iterate from $2 - \frac{n}{2}$ to find any multiples of n.
     - Use the _filter(func, seq) function to itiratively call \_is_prime(n)_ on the input list/ array.

   ```python
   def is_prime(n):
    if n < 2: return False
    for i in range (2, int(n**(1/2)) + 1):
      if n % i == 0: return False
    return True
   ```

   ```python
     prime_nums = list(filter(is_prime, nums))
   ```

---
