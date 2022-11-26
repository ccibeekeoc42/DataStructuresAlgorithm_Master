# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)
- [Dynamic Programming](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#dynamic-programming)

---

#### Arrays & Strings

1. [**Max Value**] Write a function that takes in a list/ array of numbers and returns the maximum value in the array. Solve without any build in methods.

   - [Video Walkthrough](https://www.youtube.com/watch?v=fydPf6rO5-E)

   ```python
   def max_value(nums):
   max_num = -float('inf')
   for n in nums:
     if n > max_num:
     max_num = n
   return max_num
   ```

2. [**Prime Numbers**] Write a function that takes in a list/ array of numbers and returns an array with only the prime numbers from the original list/ array. If there are no primes, it returns an empty list.

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

3. [**Uncompress**] Write a function that takes in a compessed version of a string and uncompresses/ expands it out completely. For example, if the input is `2a3b` it'll return `aabbb`.

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

   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

4. [**Compress**] Write a function that takes in a uncompessed version of a string and compresses it. For example, if the input is `ccaaatsss` it'll return `2c3at3s`.

   ```python
   def uncompress(s):
    s_out = ''
    l,r = 0,0
    while r < len(s):
      while r< len(s) and s[l]==s[r]:
        r += 1
      s_out += str(r-l) + s[l] if (r-l) > 1 else s[l]
      l = r
    return s_out
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

5. [**Anagrams**] Write a function that takes in two strings and returns a boolean indicating whether both strings are anagrams or not. For example, the strings `monkeyswrite` and `newyorktimes` are anagrams so the function should return `True`.

   ```python
   def anagrams(s1, s2):
    memo = {}
    for c in s1:
      if c not in memo:
        memo[c] = 0
      memo[c] += 1
    for c in s2:
      if c not in memo:
        memo[c] = 0
      memo[c] -= 1
    for item in memo:
      if memo[item] != 0:
        return False
    return True
   ```

   `METHOD #2`

   ```python
   def anagrams2(s1, s2):
    from collections import Counter
    return Counter(s1) == Counter(s2)
   ```

   `METHOD #3`

   ```python
   def anagrams3(s1, s2):
    return sorted(s1) == sorted(s2)
   ```

   ```
     n is the length of s1
     m is the length of s2
     Time: O(n+m)
     Space: O(n+m)
   ```

6. [**First Unique Character**] Write a function that takes a string and returns the index of the first unique character in the string.

   ```python
   def firstUniqueCharacter(s):
    memo = {}
    for i,char in enumerate(s):
      if char not in memo:
        memo[char] = i
      else:
        memo[char] = -1
    for item in memo:
      if memo[item] != -1:
        return memo[item]
    return -1
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

7. [**Find Duplicates**] Write a function that takes a list of numbers and returns a list containing all the duplicates (occurs exactly twice) in the input list.

   ```python
   def findDuplicates(nums):
    memo = {}
    for n in nums:
      if n not in memo:
        memo[n] = 0
      memo[n] += 1
    return [key for (key, value) in memo.items() if value == 2]
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

8. [**Most Frequent Character**] Write a function that takes a string and returns the most frequent character in that string and its number of occurance. For example, the string `mississippi` has the most frequent character `i` or `s` and they both occur `4` times.

   ```python
   def mostFrequentCharacter(s):
    memo = {}
    for c in s:
      if c not in memo:
        memo[c] = 0
      memo[c] += 1
    # finding the max
    max_key, max_value = None, 0
    for item in memo:
    if memo[item] > max_value:
      max_key, max_value = item, memo[item]
    return (max_key, max_value)
   ```

   `METHOD #2`

   ```python
   def mostFrequentCharacter(s):
    from collections import Counter
    memo = Counter(s)
    # finding the max
    max_key, max_value = None, 0
    for c in s:
    if best is None or memo[c] > memo[max_key]:
      max_key, max_value = c, memo[c]
    return (max_key, max_value)
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

9. [**Two Sum**] Write a function that takes a list and a target sum and returns a pair of unique indices of numbers that add up to the target sum.

   ```python
   def twoSum(nums, target):
    memo = {}
    for i, n in enumerate(nums):
      diff = target - n
      if diff in memo:
        return (memo[diff], i)
      memo[n] = i
   ```

   ```
     n is the length of the list
     Time: O(n)
     Space: O(n)
   ```

10. [**Two Prod**] Write a function that takes a list and a target product and returns a pair of unique indices of numbers that multiply up to the target product.

    ```python
    def twoProd(nums, target):
     memo = {}
     for i, n in enumerate(nums):
       comp = int(target / n)
       if comp in memo:
         return (memo[comp], i)
       memo[n] = i
    ```

    ```
      n is the length of the list
      Time: O(n)
      Space: O(n)
    ```

11. [**Two Prod**] Write a function that takes in two lists and returns a new list containing elements that are in both lists.

    ```python
    def intersection(a, b):
     result = []
     for item in b:
       if item in a:
         result.append(item)
     return result
    ```

    ```python
    def intersection(a, b):
     a = set(a)
     return [n for n in b if n in a]
    ```

    ```
      n is the length of list a
      m is the length of list b
      Time: O(n*m)
      Space: O(min(n,m))
    ```

12. [**Move Zeros**] Write a function that takes a list of numbers and rearranges the elements such that 0s appear at the end. This should be done inplace without creating a new list.

```python
def moveZeros(nums):
 l,r = 0, len(nums)-1
 while l < r:
   while nums[l] != 0:
     l += 1
   while nums[r] == 0:
     r -= 1
   nums[l], nums[r] = nums[r], nums[l]
   l += 1
   r -= 1
 return nums
```

```python
def moveZeros(nums):
 idx = 0
 for i in range(len(nums)):
   if nums[i] != 0:
     nums[idx] = nums[i]
     idx += 1
 for i in range(idx, len(nums)):
   nums[i] = 0
 return nums
```

```
  n is the length of list
  Time: O(n)
  Space: O(1)
```

---

#### Dynamic Programming

1. [**Edit Distance**] Given two strings, write a function to compute the edit distance between both strings. Meaning how many changes to be made on one string to make it identical to the other string. Example, the edit distance of the two strings `pale` and `bale` is `1` because replacing the `p` with a `b` makes them equal.

   ```python
   def computeEditDistance(s, t):
    memo = {}
    def recurse(i, j):
      if (i,j) in memo:
        return memo[(i,j)]
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
      memo[(i,j)] = result
      return result
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
