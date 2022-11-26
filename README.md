# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)
- [Dynamic Programming](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#dynamic-programming)

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

3. [Uncompress] Write a function that takes in a compessed version of a string and uncompresses/ expands it out completely. For example, if the input is `2a3b` it'll return `aabbb`.

   ```python
   def uncompress(s):
    s_out = ''
    l,r = 0,0
    while r < len(s):
      while s[r].isnumeric():
        r += 1
      s_out += s[r] * int(s[l:r])
      r += 1
      l = r
    return s_out
   ```

   ```python
     s = "2c3a1t" #ccaaat
     print(uncompress(s))
   ```

---

#### Dynamic Programming

1. [Edit Distance] Given two strings, write a function to compute the edit distance between both strings. Meaning how many changes to be made on one string to make it identical to the other string. Example, the edit distance of the two strings `pale` and `bale` is `1` because replacing the `p` with a `b` makes them equal.

   ```python
   def computeEditDistance(s, t):
    def recurse(i, j):
      if i == 0:
        result = j
      elif j == 0:
        result = i
      elif s[i-1] == t[j-1]:
        result = recurse(i-1, j-1)
      else:
        subCost = 1 + recurse(i-1, j-1)
        delCost = 1 + recurse(i-1, j)
        insCost = 1 + recurse(i, j-1)
        result = min(subCost, delCost, insCost)
    return recurse(len(s), len(t))
   ```

   `METHOD #2`

   ```python
   def computeEditDistance2(s, t):
    dp = [[0 for j in range(len(t)+1)] for i in range(len(s)+1)]
    for i in range(len(s)+1):
      for j in range(len(t)+1):
        if i == 0:
          dp[i][j] = j
        elif j == 0:
          dp[i][j] = i
        elif s[i-1] == t[j-1]:
          dp[i][j] = dp[i-1][j-1]
        else:
          subCost = 1 + dp[i-1][j-1]
          delCost = 1 + dp[i-1][j]
          insCost = 1 + dp[i][j-1]
          dp[i][j] = min(subCost, delCost, insCost)
    return dp[-1][-1]
   ```

---
