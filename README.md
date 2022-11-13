# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)

---

#### Arrays & Strings

1. [Max Value] Write a function that takes in a list/ array of numbers and returns the maximum value in the array. Solve without any build in methods.

   - [Video Walkthrough](https://www.youtube.com/watch?v=fydPf6rO5-E)

   ```python
   def max_value(nums):
   max_num = -float('inf')
   for n in nums:
     if n > max_num:
     max_num = n
   return max_num
   ```

2. [Prime Numbers] Write a function that takes in a list/ array of numbers and returns an array with only the prime numbers from the original list/ array. If there are no primes, it returns an empty list.

   ```python
   def is_prime(n):
    if n < 2: return False
    for i in range (2, int(n**(1/2)) + 1):
      if n % i == 0: return False
    return True
   ```

   ```python
    nums = [1,7, 17,4,4,2,8,10,9]
    prime_nums = list(filter(is_prime, nums))
   ```

3. Write a function that takes in a ....

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
