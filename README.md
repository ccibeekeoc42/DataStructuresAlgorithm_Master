# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

---

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)
- [Binary Search](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#binary-search)
- [Stacks & Queues](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#stacks--queues)
- [Linked Lists](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#linked-lists)
- [Binary Trees](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#binary-trees)
- [Binary Search Trees](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#binary-search-trees)
- [Graphs](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#graphs)
- [Dynamic Programming](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#dynamic-programming)
- [Tries](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#tries)
- [Bitwise Operations](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#bitwise-operations)
- [Sorting Algorithms](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#sorting-algorithms)
- [Extras](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#extras)
- [Tips & Tricks](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#tips--tricks)

---

### Arrays & Strings

1. [[**Max Value**](https://www.youtube.com/shorts/Kip91QZa8ik)] Write a function that takes in a list/ array of numbers and returns the maximum value in the array. Solve without any build in methods.

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

5. [**Reverse String**] [[**Leetcode 344**](https://leetcode.com/problems/reverse-string/)] [[**Leetcode 151**](https://leetcode.com/problems/reverse-words-in-a-string/)] Write a function that takes in a list of strings and returns the reverse of the list of strings. For example, if the input is `[hello]` it'll return `[olleh]`.

   ```python
   def reverseString(s):
    l,r = 0,len(s)-1
    while l < r:
      s[l], s[r] = s[r], s[l]
      l += 1
      r -= 1
    return s
   ```

   ```python
   def reverseString(s):
    return (' '.join(s.split()[::-1]))
   ```

   ```python
   def reverseString(s):
    return ' '.join(reversed(s.split()))
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(1)
   ```

6. [**Rotate String**] [[**Leetcode 796**](https://leetcode.com/problems/rotate-string/description/)] Given two strings `s` and `goal`, write a function that returns a boolean indicating whether or not `s` can become `goal` after some number of shift.

   ```python
   def rotateString(s, goal):
    return (len(s) == len(goal) and goal in s+s)
   ```
   ```
     n is the length of s
     Time: O(n)
     Space: O(1)
   ```

7. [**Anagrams**] [[**Leetcode 242**](https://leetcode.com/problems/valid-anagram/)] Write a function that takes in two strings and returns a boolean indicating whether both strings are anagrams or not. For example, the strings `monkeyswrite` and `newyorktimes` are anagrams so the function should return `True`.

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

   ```python
   def anagrams3(s1, s2):
    if len(s) != len(t): return False
    memo = [0]*26
    for c in s: memo[ord(c) - ord('a')] += 1
    for c in t: memo[ord(c) - ord('a')] -= 1
    for item in memo:
      if memo[item] != 0: return False
    return True
   ```

   ```
     n is the length of s1
     m is the length of s2
     Time: O(n+m)
     Space: O(n+m)
   ```

8. [**First Unique Character**] [[**Leetcode 387**](https://leetcode.com/problems/first-unique-character-in-a-string/)] Write a function that takes a string and returns the index of the first unique character in the string.

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

9. [**Single Number II**] [[**Leetcode 137**](https://leetcode.com/problems/single-number-ii/)] Given an integer array `nums` where every element appears three times except for one, which appears exactly once. Write a function to find this single element and return it.

   ```python
   def singleNumber(nums):
    memo = {}
    for num in nums:
      if num not in memo: memo[num] = 0
      memo[num] += 1
    for item in memo:
      if memo[item] == 1: return item
   ```
   ```
     n is the length of s
     Time: O(n)
     Space: O(n)
   ```

10. [**Contains Duplicates**] [[**Leetcode 217**](https://leetcode.com/problems/contains-duplicate/)] Write a function that takes in a list of numbers and returns `True` if the list contains a duplicate and `False` otherwise.

   ```python
   def containsDuplicate(nums):
    memo = {}
    for n in nums:
      if n in memo:
        return True
      memo[n] = 1
    return False
   ```

   ```python
   def containsDuplicate(nums):
    memo = set(nums)
    return len(memo) != len(nums)
   ```

   ```python
   def containsDuplicate(nums):
    from collections import Counter
    c = Counter(nums)
    for item in c:
      if c[item] > 1: return True
    return False
   ```

   ```
     n is the length of the list
     Time: O(n)
     Space:O(n)

   ```

11. [**Contains Duplicates II**] [[**Leetcode 219**](https://leetcode.com/problems/contains-duplicate-ii/)] Write a function that takes in a list of numbers and a constant `k` and returns `True` if the list contains a set duplicates whose indicies are also at most `k` distance but returns `False` otherwise.

   ```python
   def containsDuplicateII(nums, k):
    memo = {}
    for i,n in enumerate(nums):
      if n in memo and i - memo[n] <= k:
        return True
      memo[n] = i
    return False
   ```

   ```
     n is the length of the list
     Time: O(n)
     Space:O(n)

   ```

12. [**Find Duplicates**] Write a function that takes a list of numbers and returns a list containing all the duplicates (occurs exactly twice) in the input list.

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

13. [**Majority Element**] [[**Leetcode 219**](https://leetcode.com/problems/majority-element/)] Given an array `nums` of size `n`, write a function to return the majority element. Majority element is the element that appears more than half the time in the array.

    ```python
    def majorityElement(nums):
      nums.sort()
      return nums[(len(nums)-1)//2]
    ```
    ```python
    def majorityElement(nums):
      memo = {}
      for num in nums:
        if num not in memo: memo[num] = 0
        memo[num] += 1
        if memo[num] > len(nums)/2: return num
    ```
    ```
      n is the length of s
      Time: O(n)
      Space: O(n)
    ```

14. [**Most Frequent Character**] Write a function that takes a string and returns the most frequent character in that string and its number of occurance. For example, the string `mississippi` has the most frequent character `i` or `s` and they both occur `4` times.

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

15. [**Find Difference**] [[**Leetcode 389**](https://leetcode.com/problems/find-the-difference/)] Write a function that takes a string and returns the index of the first unique character in the string.

    ```python
    def findTheDifference(s, t):
      memo = {}
      for c in t:
        if c not in memo: memo[c] = 0
        memo[c] += 1
      for c in s:
        memo[c] -= 1
      for item in memo:
        if memo[item] != 0:
          return item
    ```

    ```python
    def findTheDifference(s, t):
      memo = {}
      for char in (s+t):
        if char in memo:
          memo[char] += 1
        else:
          memo[char] = 1
      for item in memo:
        if memo[item] % 2 == 1:
          return item
    ```

    ```
      n is the length of s
      Time: O(n)
      Space: O(n)
    ```

16. [[**Two Sum**](https://leetcode.com/problems/two-sum/)] Write a function that takes a list and a target sum and returns a pair of unique indices of numbers that add up to the target sum.

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

17. [**Two Sum II**] [[**Leetcode 167**](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)] Write a function that takes a sorted list and a target sum and returns a pair of unique indices (1-indexed) of numbers that add up to the target sum.

    ```python
    def twoSum(nums, target):
      l, r = 0, len(nums)-1
      while l < r:
        two_sum = nums[l] + nums[r]
        if two_sum < target:
          l += 1
        elif two_sum > target:
          r -= 1
        else:
          return [l+1, r+1]
    ```

    ```
      n is the length of the list
      Time: O(n)
      Space: O(n)
    ```

18. [**3Sum**] [[**Leetcode 15**](https://leetcode.com/problems/3sum/)] Given an integer array, write a function to return all triplets `[nums[i], nums[j], nums[k]]` such that `i != j != k` and `nums[i] + nums[j] + nums[k] == 0`. The set must not contain duplicate triplets.

    ```python
    def threeSum(nums):
      result = []
      nums.sort()
      for i, num in enumerate(nums):
        if i > 0 and num == nums[i-1]: continue
        l, r = i+1, len(nums)-1
        while l < r:
          three_sum = num + nums[l] + nums[r]
          if three_sum > 0: r -= 1
          elif three_sum < 0: l += 1
          else:
            result.append([num, nums[l], nums[r]])
            l += 1
            while nums[l] == nums[l-1] and l < r:
              l += 1
      return result
    ```

    ```
      n is the length of the list
      Time: O(n)
      Space: O(n)
    ```

19. [**Two Prod**] Write a function that takes a list and a target product and returns a pair of unique indices of numbers that multiply up to the target product.

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

20. [**Max Subarray**] [[**Leetcode 53**](https://leetcode.com/problems/maximum-subarray/)] Given an integer array, Write a function to find a subarray that has the largest sum and return it (a.k.a Kadane's Algorithm).

    ```python
    def maxSubArray(nums):
      max_sum = float('-inf')
      cur_sum = 0
      for n in nums:
        cur_sum = max(cur_sum+n, n)
        max_sum = max(max_sum, cur_sum)
      return max_sum
    ```
    ```
      n is the length of the list
      Time: O(n)
      Space: O(1)
    ```

21. [**Max Product Subarray**] [[**Leetcode 152**](https://leetcode.com/problems/maximum-product-subarray/)] Given an integer array, Write a function that to find a subarray that has the largest product and return the product.

    ```python
    def maxProduct(nums):
      max_prod = float('-inf')
      cur_max = cur_min = 1
      for n in nums:
        old_max = cur_max * n
        cur_max = max(old_max, cur_min * n, n)
        cur_min = min(old_max, cur_min * n, n)
        max_prod = max(max_prod, cur_max)
      return max_prod
    ```

    ```
      n is the length of the list
      Time: O(n)
      Space: O(1)
    ```

22. [**Intersection**] [[**Leetcode 349**](https://leetcode.com/problems/intersection-of-two-arrays/)] Write a function that takes in two lists and returns a new list containing elements that are in both lists.

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

23. [**Jewels and Stones**] [[**Leetcode 771**](https://leetcode.com/problems/jewels-and-stones/)] Given two arrays, one representing `jewels` and the other representing `stones`. Write a function that returns an integer indicating how many stones are also jewels.

    ```python
    def numJewelsInStones(jewels, stones):
      count = 0
      for s in stones:
        if s in jewels: count += 1
      return count
    ```
    ```
      n is the length of list a
      m is the length of list b
      Time: O(n*m)
      Space: O(1)
    ```

24. [**Disappeared Numbers**] [[**Leetcode 448**](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)] Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return an array of all integers in that range that do not appear in `nums`. 

    ```python
    def findDisappearedNumbers(jewels, stones):
      n = len(nums)
      nums = set(nums)
      result = []
      for i in range(1, n+1):
          if i not in nums:
              result.append(i)
      return result
    ```
    ```
      n is the length of list a
      m is the length of list b
      Time: O(n*m)
      Space: O(1)
    ```

25. [**Buy Stock**] [[**Leetcode 121**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)] Given an array of numbers representing stock price at specific days, write a function that returns the maximum profit you can achieve from the transaction. You have to choose a single day to buy one stock and a different day in the future to sell.

    ```python
    def maxProfit(prices):
      max_profit, min_price = 0, float('inf')
      for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
      return max_profit
    ```
    ```python
    def maxProfit(prices):
      max_profit = 0
      l, r = 0, 1
      while r < len(prices):
        if prices[l] < prices[r]:
          profit = prices[r] - prices[l]
          max_profit = max(max_profit, profit)
        else:
          l = r
        r += 1
      return max_profit
    ```
    ```
      n is the length of the array
      Time: O(n)
      Space: O(1)
    ```

26. [**Buy Stock II**] [[**Leetcode 122**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)] Given an array of numbers representing stock price at specific days, write a function that returns the maximum profit you can achieve from the transaction. You can hold at most onse stock st a time however, you can buy and immediately sell and buy again as often as needed.

    ```python
    def maxProfit(prices):
      profit = 0
      for i in range(len(prices)-1):
        if prices[i] < prices[i+1]:
          profit += prices[i+1] - prices[i]
      return profit
    ```
    ```python
    def maxProfit(prices):
      profit = 0
      l, r = 0, 1
      while r < len(prices):
        if prices[l] < prices[r]:
          profit += prices[r] - prices[l]
        l += 1
        r += 1
      return profit
    ```
    ```
      n is the length of the array
      Time: O(n)
      Space: O(1)
    ```

27. [**Buy Stock III**] [[**Leetcode 123**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)] Given an array of numbers representing stock price at specific days, write a function that returns the maximum profit you can achieve if you can complete at most 2 transactions. You can hold at most onse stock st a time however, you can buy and immediately sell and buy again as often as needed.

    ```python
    def maxProfit(prices):
      max_profits = [0]*(len(prices)+1)
      for _ in range(2):
          best_profit = float('-inf')
          cur_profits = [0]*(len(prices)+1)
          for i, price in enumerate(prices, start=1):
              cur_profits[i] = max(cur_profits[i-1], price+best_profit)
              best_profit = max(best_profit, max_profits[i]-price)
          max_profits = cur_profits
      return max_profits[-1]
    ```
    ```
      n is the length of the array
      Time: O(n)
      Space: O(n)
    ```

28. [**Buy Stock IV**] [[**Leetcode 124**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)] Given an array of numbers representing stock price at specific days, write a function that returns the maximum profit you can achieve if you can complete at most `k` transactions. You can hold at most onse stock st a time however, you can buy and immediately sell and buy again as often as needed.

    ```python
    def maxProfit(prices, k):
      max_profits = [0]*(len(prices)+1)
      for _ in range(k):
          best_profit = float('-inf')
          cur_profits = [0]*(len(prices)+1)
          for i, price in enumerate(prices, start=1):
              cur_profits[i] = max(cur_profits[i-1], price+best_profit)
              best_profit = max(best_profit, max_profits[i]-price)
          max_profits = cur_profits
      return max_profits[-1]
    ```
    ```python
    def maxProfit(prices, k):
      def dp(i, sell, k, memo={}):
        key = (i, sell, k)
        if key in memo: return memo[key]
        if i == len(prices) or k < 0: return 0
        do_nothing = dp(i+1, sell, k, memo)
        if sell: do_something = prices[i] +  dp(i+1, not sell, k, memo) # sell
        else: do_something = -prices[i] +  dp(i+1, not sell, k-1, memo) # buy
        memo[key] = max(do_nothing, do_something)
        return memo[key]
      return dp(0, False, k)
      ```
      ```
        n is the length of the array
        Time: O(n)
        Space: O(n)
      ```

29. [**Move Zeros**] [[**Leetcode 283**](https://leetcode.com/problems/move-zeroes/)] Write a function that takes a list of numbers and rearranges the elements such that 0s appear at the end. This should be done inplace without creating a new list.

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

30. [**Move Item**] Write a function that takes a list of numbers and an integer `toMove` and rearranges the elements such that all `toMove` appear at the end. This should be done inplace without creating a new list.

    ```python
    def moveItem(nums, toMove):
      l,r = 0, len(nums)-1
      while l < r:
        while l < r and nums[r] == toMove: r-=1
        if nums[l] == toMove: nums[l], nums[r] = nums[r], nums[l]
        l += 1
      return nums
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

31. [**Rotate Array**] [[**Leetcode 189**](https://leetcode.com/problems/move-zeroes/)] Write a function that takes an array and rotates it by `k` steps where `k` is non-negative.

    ```python
    def rotate(nums, k):
      for _ in range(k):
        nums.insert(0, nums.pop())
    ```
    ```python
    def rotate(nums, k):
      nums[:] = nums[-k%len(nums):] + nums[:-k%len(nums)]
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

32. [**Remove Duplicates**] [[**Leetcode 26**](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)] Given a sorted integer array `nums`, write a function to remove all duplicates from `nums` in-place. Return the last index of the resulting array.

    ```python
    def removeElement(nums, val):
      index = 0
      for i in range(len(nums)-1):
          if nums[i] != nums[i+1]:
              nums[index] = nums[i+1]
              index += 1
      return index
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

33. [**Remove Element**] [[**Leetcode 27**](https://leetcode.com/problems/remove-element/)] Given an integer array `nums` and an integer `val`, write a function to remove all occurrences of `val` from `nums` in-place. Return the last index of the resulting array.

    ```python
    def removeElement(nums, val):
      index = 0
      for num in nums:
          if num != val:
              nums[index] = num
              index += 1
      return index
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

34. [**Monotonic Array**] [[**Leetcode 896**](https://leetcode.com/problems/monotonic-array/)] An array is monotonic if it's either monotone increasing or decreasing. Given an integer array, write a function that returns a boolean indicating whether the array is monotonic. 

    ```python
    def isMonotonic(nums):
      inc = True
      dec = True
      for i in range(len(nums)-1):
        if nums[i] > nums[i+1]: inc = False
        elif nums[i] < nums[i+1]: dec = False
      return inc or dec
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

35. [**Can Place Flowers**] [[**Leetcode 605**](https://leetcode.com/problems/can-place-flowers/)] Given an integer array `flowerbed` containing `0`'s and `1`'s representing empty and not empty respectively and an integer `n`, write a function that returns an integer indicating whether or not `n` new flower can be panted.

    ```python
    def canPlaceFlowers(nums):
      count = 0
      if (n == 0): return True
      for i in range(len(flowerbed)):
        l,r = i-1, i+1
        if (flowerbed[i] == 0) and (i == 0 or flowerbed[l] == 0) and (i == len(flowerbed) - 1 or flowerbed[r] == 0):
          count += 1
          flowerbed[i] = 1
      return count >= n
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

36. [**Container With Most Water**] [[**Leetcode 11**](https://leetcode.com/problems/container-with-most-water/)] Given an integer array where each element represents vertical lines with tha x-axis. Write a function that returns the container that can contain the most water.

    ```python
    def maxArea(height):
      max_area = 0
      l,r = 0, len(height)-1
      while (l < r):
        if height[l] < height[r]:
          max_area = max(max_area, height[l]*(r-l))
          l += 1
        else:
          max_area = max(max_area, height[r]*(r-l))
          r -= 1
      return max_area
    ```

    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

37. [**Valid Palindrome**] [[**Leetcode 125**](https://leetcode.com/problems/valid-palindrome/)] Given a phrase as a string `s`, write a function to return a boolean indicating whether or not the string is a palindrome. Ignore all none-alpha-numeric characters.

    ```python
    def isPalindrome(s):
      s = s.lower()
      l, r = 0, len(s)-1
      while l < r:
        while l < r and not s[l].isalnum(): l += 1
        while l < r and not s[r].isalnum(): r -= 1
        if s[l] != s[r]: return False
        l += 1
        r -= 1
      return True
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

38. [**Palindrome Number**] [[**Leetcode 9**](https://leetcode.com/problems/palindrome-number/)] Given an integer `x`, write a function that returns a boolean indicating whether or not the integer is a valid palindrome.

    ```python
    def isPalindrome(s):
      s = str(x)
      l,r = 0, len(s)-1
      while l < r:
          if s[l] != s[r]: return False
          l += 1
          r -= 1
      return True
    ```
    ```python
    def isPalindrome(s):
      return (str(x) == str(x)[::-1])
    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(1)
    ```

39. [**Sorted Squared**] Given a ascending-sorted array of integers, write a function that returns a new array of the same length containing the squares of the original array but also sorted in ascending order.

    ```python
    def sortedSquaredArray(nums):
      res = [0] * len(nums)
      l,r = 0, len(nums)-1
      i = len(nums)-1
      while l <= r:
        if abs(nums[l]) > abs(nums[r]):
          res[i] = nums[l]**2
          l += 1
        else:
          res[i] = nums[r]**2
          r -= 1
        i -= 1
      return res

    ```
    ```
      n is the length of list
      Time: O(n)
      Space: O(n)
    ```

---

### Binary Search

1. [**Binary Search**] How to execute binary search on sorted array.
    - Ensure to the list/ sequence is sorted in ascending order.

    ```python
    def search(nums, target):
      l, mid, r = 0, 0, len(nums)
      step = 0
      while (l <= r):
        print(f"Step{step}: {nums[l:r+1]}")
        step += 1
        mid = (l+r) // 2
        if target == nums[mid]: return mid
        elif target < nums[mid]: r = mid - 1
        else: l = mid + 1
      return f'{target} not found'

    # Driver Code
    nums, target = [1,2,3,4,5,6,7,8,9], 0
    search(nums, target)
    ```

2. [**First Bad Version**] [[**Leetcode 278**](https://leetcode.com/problems/first-bad-version/)] Given an API `isBadVersion(version)` that takes in a number in a sequence `n` and returns a boolean indicating whether or not the product version is bad. Write a function that minimizes calls to the API and finds the first bad version in the sequence. 

    ```python
    def firstBadVersion(n):
      l,r = 0,n
      while l < r:
        mid = (r+l)//2
        if isBadVersion(mid): r = mid
        else: l = mid + 1
      return r
    ```
    ```
      n is the length of list
      Time: O(log(n))
      Space: O(1)
    ```

3. [**Find Peak Element**] [[**Leetcode 162**](https://leetcode.com/problems/find-peak-element/)] Given an integer array, Write a function to return the index of the peak element.

    ```python
    def findPeak(nums):
      l,r = 0, len(nums)-1
      while l < r:
        mid = (r+l)//2
        if nums[mid] < nums[mid+1]: l = mid + 1
        else: r = mid
      return l
    ```
    ```python
    def findPeak(nums):
      l,r = 0, len(nums)-1
      while l < r:
        if nums[l] < nums[r]: l += 1
        else: r -= 1
      return r
    ```
    ```
      n is the length of list
      Time: O(log(n))
      Space: O(1)
    ```

4. [**Find Minimum in Rotated Sorted Array**] [[**Leetcode 153**](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)] Given an array of unique integers and of length `n` sorted in ascending order and rotated between `1` and `n` times, write a function to return the minimum element of this array.

    ```python
    def findMin(nums):
      l,r = 0, len(nums)-1
      while l <= r:
        mid = (r+l)//2
        if nums[mid] > nums[r]: l = mid+1
        else: r = mid
      return num[l]
    ```

    ```
      n is the length of list
      Time: O(log(n))
      Space: O(1)
    ```

5. [**Search Rotated Sorted Array**] [[**Leetcode 33**](https://leetcode.com/problems/search-in-rotated-sorted-array/)] Given a target integer and an integer array sorted in ascending order and then possibly rotated at an unknown pivote index. Write a function to return the index of the target if it exists else return `-1`.

    ```python
    def search(nums, target):
      l,r = 0, len(nums)-1
      while l <= r:
        mid = (r+l)//2
        if target == nums[mid]: return mid
        if nums[l] <= nums[mid]:
          if target > nums[mid] or target < nums[l]: l = mid + 1
          else: r = mid - 1
        else:
          if target < nums[mid] or target > nums[r]: r = mid - 1
          else: l = mid + 1
      return -1
    ```

    ```
      n is the length of list
      Time: O(log(n))
      Space: O(1)
    ```

---

### Stacks & Queues

1. [**Valid Set of Parentheses**] Given a string as input, write a function to return a boolean indicating whether or not the string has balanced parentheses. 

   ```python
   def balancedParentheses(s):
    stack = []
    for c in s:
      if c == '(': stack.append(c)
      elif c == ')':
        if len(stack) > 0: stack.pop()
        else: return False
    return len(stack) == 0
   ```
   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```
   ```python
   def balancedParentheses(s):
    count = 0
    for c in s:
      if c == '(': count += 1
      elif c == ')':
        if count > 0: count -= 1
        else: return False
    return count == 0    
   ```
   ```
     n is the length of the string
     Time: O(n)
     Space: O(1)
   ```

2. [**Balanced Brackets**] Given a string as input, write a function to return a boolean indicating whether or not the string has balanced brackets (every opener has a closer). 

   ```python
   def balancedBrackets(s):
    stack = []
    brackets = {'(':')', '{':'}', '[':']'}
    for c in s:
      if c in brackets: stack.append(brackets[c])
      else:
        if stack and stack[-1] == c: stack.pop()
        else: return False
    return len(stack) == 0
   ```
   ```python
   def balancedBrackets(s):
    stack = []
    for c in s:
      if c == '(' or c == '{' or '[': stack.append(c)
      elif len(s) == 0: return False
      else:
        if ((c == ')' and stack[-1] == '(') or 
            (c == '}' and stack[-1] == '{') or
            (c == ']' and stack[-1] == '[')): stack.pop()
    return len(stack) == 0
   ```
   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

3. [**Backspace String Compare**] [[**Leetcode 844**](https://leetcode.com/problems/backspace-string-compare/)] Given two strings `s` and `t`, write a function that returns a boolean indicating whether or not both strings are equal. `#` represents backspace character.

   ```python
   def backspaceCompare(s, t):
    stack_s, stack_t = [], []
    for c in s:
      if c != '#': stack_s.append(c)
      elif len(stack_s): stack_s.pop()
    for c in t:
      if c != '#': stack_t.append(c)
      elif len(stack_t): stack_t.pop()
    return stack_s == stack_t
   ```
   ```
     n is the length of s
     m is the length of t
     Time: O(n+m)
     Space: O(n+m)
   ```

4. [**Remove Consecutive Duplicates**] Given a string, return a string where ll consecutive duplicates have been removed. Example, for the input string `abbccwaabba` the function would return `awa`.

   ```python
   def removeDuplicates(s):
    stack = [s[0]]
    for i in range(1, len(s)):
      if len(stack) and stack[-1] == s[i]:
        while i < len(s) and s[i-1] == s[i]:
          i += 1
        stack.pop()
      else:
        stack.append(s[i])
    return "".join(stack)
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

5. [**Is Subsequence**] [[**Leetcode 392**](https://leetcode.com/problems/is-subsequence/)] Write a function that takes in two strings `s` and `t` and returns a boolean indicating whether `s` is a subsequence of `t`.

    ```python
    def isSubsequence(s, t):
      if len(s) == 0: return True
      if len(t) == 0: return False
      q = []
      for c in s: q.append(c)
      for c in t:
        if len(q) == 0: return True
        if c == q[0]: q.pop(0)
      return False if len(q) != 0 else True
    ```

    ```python
    def isSubsequence(s, t):
      idx_t, idx_s = 0, 0
      while idx_t < len(t) and idx_s < len(s):
        if t[idx_t] == s[idx_s]:
          idx_s += 1
        idx_t += 1
      return idx_s == len(s)
    ```

    ```python
    def isSubsequence(s, t):
      t = iter(t)
      return all(c in t for c in s)
    ```

    ```
      n is the length of string s
      m is the length of string t
      Time: O(max(n,m))
      Space: O(1)
    ```

6. [**Expand Braces**] Given a compressed string, write a function that returns the expanded version of the string. Example `n{sub_string}` the substring enclosed in curley braces should be repeated `n` times.

   ```python
   def expandBraces(s):
    stack = []
    result = ''
    for c in s:
      if c == '{': continue
      elif c == '}':
        temp = ''
        while stack[-1].isalpha():
          temp = stack.pop() + temp
        num = stack.pop()
        stack.append(temp * int(num))
        continue
      stack.append(c)
    return ''.join(stack)
   ```

   ```
     s is the length of the string
     m is the number of brace pairs
     Time: O((9^m)*s)
     Space: O((9^m)*s)
   ```

7. [**Nesting Brackets**] Given a string of brackets, wrute a function to return an integer representing the nesting score based on the rules below.

    ```
      [] -> 1
      [][][] -> 3
      [[]] -> 2
    ```
   ```python
   def nestingScore(s):
    stack = [0]
    for c in s:
      if c == '[': stack.append(0)
      elif c == ']':
        temp = stack.pop()
        if temp == 0: stack[-1] += 1
        else: stack[-1] += (temp * 2)
    return stack[-1]
   ```
   ```
     n is the length of the string
     Time: O(n)
     Space: O(nS)
   ```

---


### Linked Lists

1. [**Create Linked List**] Create a linked list of the following values `A->B->C->D`.

   ```python
   class Node:
    def __init__(self, val):
      self.val = val
      self.next = None

   a, b, c, d = Node('A'), Node('B'), Node('C'), Node('D')
   a.next, b.next, c.next, = b, c, d
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

2. [**Append Value**] Given the head of a linked list like `A->B->C->D` and a Node value to append like `z`. Write a function to append the value to the end of the linked list.

   ```python
   def append(head, data):
    '''Iterative Approach'''
    new_node, cur = Node(data), head
    while cur.next:
      cur = cur.next
    cur.next = new_node
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(1)
   ```

3. [**Prepend Value**] Given the head of a linked list like `A->B->C->D` and a Node value to prepend (add to front) like `z`. Write a function to prepend the value to the front of the linked list.

   ```python
   def prepend(head, data):
    '''Iterative Approach'''
    new_node = Node(data)
    new_node.next = head
    return new_node
   ```

   ```
     n is the length of the linked list.
     Time: O(1)
     Space: O(1)
   ```

4. [**Print Linked List**] Given the head of a linked list like `A->B->C->D`. Write a function to print all values in the list in the right order.

   ```python
   def printList(head):
    '''Iterative Approach'''
    cur = head
    while cur:
      print(cur.val, end="->")
      cur = cur.next
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(1)
   ```

   ```python
   def printList(head):
    '''Recursieve Approach'''
    if not head: return None
    print(head.val, end="->")
    printList(head.next)
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

5. [**Linked List Values**] Given the head of a linked list like `A->B->C->D`. Write a function to return all values in the list in the right order in an array/ list.

   ```python
   def LinkedListValues(head):
    '''Iterative Approach'''
    cur, result = head, []
    while cur:
      result.append(cur.val)
      cur = cur.next
    return result
   ```

   ```python
   def LinkedListValues(head):
    '''Recursieve Approach'''
    if not head: return []
    return [head.val, *LinkedListValues(head.next)]
   ```

   ```python
   def LinkedListValues(head):
    '''Recursieve Approach'''
    result = []
    def fillValues(head, values):
      if not head: return
      values.append(head.val)
      fillValues(head.next, values)
    fillValues(head, result)
    return result
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

6. [**Create Linked List**] Given a list/ array of values like `[1, 2, 3, 5]`. Write a function to create a linked list containing each item of the list as nodes and return the head of the linked list. The example above should return `1->2->3->5`.

   ```python
   def createLinkedList(values):
    '''Iterative Approach'''
    dummy = Node(None)
    cur = dummy
    for item in values:
      cur.next = Node(item)
      cur = cur.next
    return dummy.next
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

   ```python
   def createLinkedList(values):
    '''Recursieve Approach'''
    if not values or len(values)==0: return None
    head = Node(values[0])
    head.next = createLinkedList(values[1:])
    return head
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n^2)
   ```

   ```python
   def createLinkedList(values, i=0):
    '''Recursieve Approach'''
    if i >= len(values): return None
    head = Node(values[i])
    head.next = createLinkedList(values, i+1)
    return head
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

7. [**Linked List to String**] Given the head of a linked list like `A->B->C->D`. Write a function to return all values in the list in the right order as a string

   ```python
   def LinkedListValues(head):
    '''Iterative Approach'''
    cur, result = head, ''
    while cur:
      result += cur.val
      cur = cur.next
    return result
   ```

   ```python
   def LinkedListValues(head):
    '''Recursieve Approach'''
    if not head: return ''
    return head.val + LinkedListValues(head.next)
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

8. [**Sum Linked List**] Given the head of a linked list like `1->2->3->4`. Write a function to return the sum of all values in the list.

   ```python
   def sumList(head):
    '''Iterative Approach'''
    cur, result = head, 0
    while cur:
      result += cur.val
      cur = cur.next
    return result
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(1)
   ```

   ```python
   def sumList(head):
    '''Recursieve Approach'''
    if not head: return 0
    return head.val + sumList(head.next)
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

9. [**Palindrome List**] Given the head of a linked list like `r->a->c->e->c->a->r`. Write a function that returns a boolean indicating whether or not the linked list is a palindrome. A palindrome is a sequence that reads the same forward and backwards.

   ```python
   def isPalindrome(head):
    '''Iterative Approach'''
    cur, values = head, []
    while cur:
      values.append(cur.val)
      cur = cur.next
    return values == values[::-1]
   ```

   ```python
   def isPalindrome2(head):
    '''Recursieve Approach'''
    def listValues(head):
      if not head: return []
      return [head.val, *LinkedListValues(head.next)]
    values = listValues(head)
    return values == values[::-1]
   ```

   ```python
   def isPalindrome3(head):
    '''Iterative Approach'''
    values = []
    while head:
      values.append(head.val)
      head = head.next

    l, r = 0, len(values)-1
    while l < r:
      if values[l] != values[r]:
        return False
      l += 1
      r -= 1
    return True
   ```

   ```
     n is the length of the linked list.
     Time: O(n)
     Space: O(n)
   ```

10. [**Find Value**] Given the head of a linked list and a target value like `a->d->c->d->e` and `c`. Write a function that returns a boolean indicating whether or not the traget value is contained in the linked list.

    ```python
    def findValue(head, target):
     '''Iterative Approach'''
     if not head: return False
     cur = head
     while cur:
       if cur.val == target:
         return True
       cur = cur.next
     return False
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def findValue(head, target):
     '''Recursieve Approach'''
     if not head: return False
     if head.val == target: return True
     return findValue(head.next, target)
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(n)
    ```

11. [**Get Node Value**] Given the head of a linked list and an index value like `a->d->c->d->e` and `2`. Write a function that returns the value at that specific index. In this example, the value `c` is at index `2`. Return `None` otherwise.

    ```python
    def getNodeValue(head, index):
     '''Iterative Approach'''
     cur, count = head, 0
     while cur:
       if count == index:
         return cur.val
       cur, count = cur.next, count + 1
     return None
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def getNodeValue(head, index):
     '''Recursieve Approach'''
     if not head: return None
     if index == 0: return head.val
     return getNodeValue(head.next, index-1)
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(n)
    ```

12. [**Middle Value**] Given the head of a linked list like `a->d->c->d->e`. Write a function that returns the value of the middle node in the linked list. The example above should return `c`. if there's an even number of nodes, it should return the second middle.

    ```python
    def middleValue(head):
     '''Iterative Approach'''
     cur, values = head, []
     while cur:
       values.append(cur.val)
       cur = cur.next
     return values[len(values)//2]
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(n)
    ```

    ```python
    def middleValue(head):
     '''Runner Approach'''
     slow, fast = head, head
     while fast and fast.next:
       slow, fast = slow.next, fast.next.next
     return slow.val
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(1)
    ```

13. [**Linked List Cycle**] Given the head of a linked list like `a->b->c->d->b`. Write a function that returns a boolean indicating whether or not the list contains a cycle.

    ```python
    def listHasCycle(head):
      '''Iterative Approach'''
      cur, memo = head, set()
      while cur:
        if cur in memo: return True
        memo.add(cur)
        cur = cur.next
      return False
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(n)
    ```

    ```python
    def listHasCycle(head):
      '''Runner Approach'''
      slow, fast = head, head
      while fast and fast.next:
        slow, fast = slow.next, fast.next.next
        if slow == fast: return True
      return slow.val
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(1)
    ```

14. [**Reverse List**] [[**Leetcode 206**](https://leetcode.com/problems/reverse-linked-list/)] Given the head of a linked list like `a->b->c->d->e`. Write a function that reverses the order of the nodes in the list. The example above should return `e->d->c->b->a`.

    ```python
    def reverseList(head):
      '''Iterative Approach'''
      prev, cur = None, head
      while cur:
        cur.next, prev, cur = prev, cur, cur.next
      return prev
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def reverseList(head, prev=None):
      '''Recursieve Approach'''
      if not head: return prev
      next = head.next
      head.next = prev
      return reverseList(next, head)
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(n)
    ```

15. [**Remove Duplicates**] [[**Leetcode 83**](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)] Given the head of a linked list like `a->b->b->c->d->d->e`. Write a function that returns the list but with each item occuring only once. The example above should return `a->b->c->d->e`.

    ```python
    def removeDuplicates(head):
      '''Works only if the list is sorted'''
      dummy, dummy.next = Node(None), head
      prev, cur = dummy, head
      while cur:
        if cur.val == prev.val:
          prev.next = cur.next
        else:
          prev = cur
        cur = cur.next
      return dummy.next
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def removeDuplicates(head):
      '''Works for unsorted list also'''
      prev, cur, memo = None, head, set()
      while cur:
        if cur.val in memo:
          prev.next = cur.next
        else:
          memo.add(cur.val)
          prev = cur
        cur = cur.next
      return head
    ```

    ```
      n is the length of the linked list.
      Time: O(n)
      Space: O(n)
    ```

16. [**Zipper List**] Given the heads of two linked lists `a->b` and `w->x->y->z`. Write a function that returns a zippered list containing alternating nodes of both lists. The example above should return `a->w->b->x->y->z`.

    ```python
    def zipperLists(head1, head2):
      '''Iterative Approach'''
      cur1, cur2, tail = head1.next, head2, head1
      count = 0
      while cur1 and cur2:
        if count % 2 == 0:
          tail.next = cur2
          cur2 = cur2.next
        else:
          tail.next = cur1
          cur1 = cur1.next
        count += 1
        tail = tail.next
      if cur1: tail.next = cur1
      if cur2: tail.next = cur2
      return head1
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(min(n,m))
    Space: O(1)
    ```

    ```python
    def zipperLists(head1, head2):
      '''Recursive Approach'''
      if not head1 and not head2: return None
      if not head1: return head2
      if not head2: return head1

      n1 = head1.next
      n2 = head2.next
      head1.next = head2
      head2.next = zipperLists(n1, n2)
      return head1
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(min(n,m))
    Space: O(min(n,m))
    ```

17. [**Merge Two Sorted Lists**] [[**Leetcode 21**](https://leetcode.com/problems/merge-two-sorted-lists/)] Given the heads of two sorted linked lists `1->2->6->10` and `3->7->8->12`. Write a function that returns a single sorted linked list from the two inpute lists. The example above should return `1->2->3->6->7->8->10->12`.

    ```python
    def mergeLists(head1, head2):
      '''Iterative Approach'''
      dummy = Node(None)
      cur = dummy
      while head1 and head2:
        if head1.val < head2.val:
          cur.next = head1
          head1 = head1.next
        else:
          cur.next = head2
          head2 = head2.next
        cur = cur.next
      if head1: cur.next = head1
      if head2: cur.next = head2
      return dummy.next
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(min(n,m))
    Space: O(1)
    ```

    ```python
    def mergeLists(head1, head2):
      '''Recursive Approach'''
      if not head1 and not head2: return None
      if not head1: return head2
      if not head2: return head1

      if head1.val < head2.val:
        n1 = head1.next
        head1.next = mergeLists(n1, head2)
        return head1
      else:
        n2 = head2.next
        head2.next = mergeLists(head1, n2)
        return head2
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(min(n,m))
    Space: O(min(n,m))
    ```

18. [**Univalue List**] Given the head of a linked list like `2->2->2->2`. Write a function that returns a boolean indicating whether the linked list contains exactly one unique value.

    ```python
    def isUniqueValue(head):
      '''Iterative Approach'''
      cur = head
      while cur:
        if head.val != cur.val: return False
        cur = cur.next
      return True
    ```

    ```python
    def isUniqueValue(head):
      '''Iterative Approach'''
      while head.next:
        if head.val != head.next.val: return False
        head = head.next
      return True
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def isUniqueValue(head, prev_val=None):
      '''Recursive Approach'''
      if not head: return True
      if prev_val is None or head.val == prev_val:
        return isUniqueValue(head.next, prev_val=head.val)
      else:
        return False
    ```

    ```python
    def isUniqueValue(head, prev_val=None):
      '''Recursive Approach'''
      if not head: return True
      if prev_val is not None and head.val != prev_val:
        return False
      else:
        return isUniqueValue(head.next, prev_val=head.val)
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(n)
    ```

19. [**Longest Streak**] Given the head of a linked list like `3->3->9->9->9->2`. Write a function that returns the length of the longest consecutive streak of the same value. The example above should return `3`.

    ```python
    def longestStreak(head):
      '''Iterative Approach'''
      count, max_count = 0, 0
      p1, p2 = head, head
      while p1 and p2:
        if p2.val == p1.val:
          count += 1
          p2 = p2.next
        else:
          count = 0
          p1 = p2
        max_count = max(max_count, count)
      return max_count
    ```

    ```python
    def longestStreak(head):
      '''Iterative Approach'''
      count, max_count = 0, 0
      p1, p2 = head, head
      while p1 and p2:
        while p2 is not None and p1.val == p2.val:
          count += 1
          p2 = p2.next
        max_count = max(max_count, count)
        count = 0
        p1 = p2
      return max_count
    ```

    ```python
    def longestStreak(head):
      '''Iterative Approach'''
      count, max_count = 0, 0
      prev_val, cur = None, head
      while cur:
        if cur.val == prev_val:
          count += 1
        else:
          count = 1
        max_count = max(max_count, count)
        prev_val = cur.val
        cur = cur.next
      return max_count
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

20. [**Remove First Matching Node**] Given the head of a linked list like `3->3->9->` and a node value to delete like `9`. Write a function that deletes the first occuring node with that value. The example above should return `3->3->`.

    ```python
    def removeNode(head, target_val):
      '''Iterative Approach'''
      if head.val == target_val:
        return head.next
      prev, cur = None, head
      while cur:
        if cur.val == target_val:
          prev.next = cur.next
          break
        prev, cur = cur, cur.next
      return head
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def removeNode(head, target_val):
      '''Recursive Approach'''
      if not head: return None
      if head.val == target_val:
        return head.next
      head.next = remove_node(head.next, target_val)
      return head
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(n)
    ```

21. [**Remove All Matching Nodes**] Given the head of a linked list like `3->9->3->9->` and a node value to delete like `9`. Write a function that deletes all ocurrance of the nodes with that value. The example above should return `3->3->`.

    ```python
    def removeNode(head, target_val):
      '''Iterative Approach'''
      if head.val == target_val:
        return head.next
      prev, cur = None, head
      while cur:
        if cur.val == target_val:
          prev.next = cur.next
        prev, cur = cur, cur.next
      return head
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

22. [**Remove Nth Node from End of Lists**][[**Leetcode 19**](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)] Given the heads of a linked list, write a function to remove the nth node from the end of the list and return it's head.

    ```python
    def removeNthFromEnd(head, n):
      dummy, dummy.next = ListNode(), head
      slow, fast = dummy, head
      for _ in range(n):
        fast = fast.next
      while fast:
        slow, fast = slow.next, fast.next
      slow.next = slow.next.next
      return dummy.next
    ```
    ```
    n is the length of list1.
    m is the length of list2
    Time: O(max(n,m))
    Space: O(max(n,m))
    ```

23. [**Insert Node**] Given the head of a linked list like `3->3->9->`, a value like `6` and and index like `2`. Write a function that insertes the given value in the specified index of the linked list. The example above should return `3->3->6->9`.

    ```python
    def insertNode(head, value, index):
      '''Iterative Approach'''
      value_node = Node(value)
      if index == 0:
        value_node.next = head
        return value_node
      cur, count = head, 0
      while cur:
        if count = index-1:
          temp = cur.next
          cur.next = value_node
          value_node.next = temp
        count += 1
        cur = cur.next
      return head
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(1)
    ```

    ```python
    def insertNode(head, value, index, count=0):
      '''Recursive Approach'''
      if index == 0:
        new_head = Node(value)
        new_head.next = head
        return new_head
      if not head: return None
      if count = index-1:
        temp = head.next
        head.next = Node(value)
        head.next.next = temp
      insertNode(head.next, value, index, count+1)
      return head
    ```

    ```
    n is the length of the linked list.
    Time: O(n)
    Space: O(n)
    ```

24. [[**Add Lists**](https://leetcode.com/problems/add-two-numbers/)] Given the heads of two linked lists (with each list representing a number written in the reverse order. For example the numbers `621` and `354` would be given as `1->2->6` and `4->5->3`. Write a function that returns the head of a new linked list representing the sum of both input lists. The example above would result in `5->7->9` which is `975`.

    ```python
    def addLists(head1, head2):
      '''Iterative Approach'''
      cur1, cur2, carry = head1, head2, 0
      dummy = Node(None)
      tail = dummy
      while cur1 or cur2 or carry:
        val1 = cur1.val if cur1 else 0
        val2 = cur2.val if cur2 else 0

        value = (val1 + val2 + carry) % 10
        carry = (val1 + val2 + carry) // 10
        tail.next = Node(value)

        cur1 = cur1.next if cur1 else None
        cur2 = cur2.next if cur2 else None
        tail = tail.next
      return dummy.next
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(max(n,m))
    Space: O(max(n,m))
    ```

    ```python
    def addLists(head1, head2, carry=0):
      '''Recursive Approach'''
      if not head1 and not head2 and not carry: return None
      val1 = head1.val if head1 else 0
      val2 = head2.val if head2 else 0

      value = (val1 + val2 + carry) % 10
      carry = (val1 + val2 + carry) // 10
      result = Node(value)

      n1 = head1.next if head1 else None
      n2 = head2.next if head2 else None
      result.next = addLists(n1, n2, carry)

      return result
    ```

    ```
    n is the length of list1.
    m is the length of list2
    Time: O(max(n,m))
    Space: O(max(n,m))
    ```

---

### Binary Trees

1. [**Create Binary Tree**] Create a binary tree of the below structure.

   ```python
     '''
          A
         / \
        B   C
       / \   \
      D   E   F
     '''
   ```

   ```python
   class Node:
   def __init__(self, val=None):
     self.val = val
     self.left = None
     self.right = None

   a,b,c,d,e,f = Node('A'), Node('B'), Node('C'), Node('D'), Node('E'), Node('F')
   a.left, a.right = b, c
   b.left, b.right = d, e
   c.right = f
   ```

   ```
     n is the number of nodes.
     Time: O(n)
     Space: O(n)
   ```

2. [**Depth First Values**] Given the root of a binary tree, write a function to print all values in the tree using a depth first search approach (DFS).

   ```python
   def depthFirstValues(root):
     '''Iterative Approach'''
     s = [root]
     while s:
       cur = s.pop()
       print(cur.val, end=",")
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
   ```

   ```python
   def depthFirstValues(root):
    '''Recursive Approach'''
    if not root: return
    print(root.val, end=",")
    depthFirstValues(root.left)
    depthFirstValues(root.right)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

3. [**Breadth First Values**] Given the root of a binary tree, write a function to print all values in the tree using a breadth first search approach (BFS).

   ```python
   def breadthFirstValues(root):
     '''Iterative Approach'''
     q = [root]
     while q:
       cur = q.pop(0)
       print(cur.val, end=",")
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n^2)
   ```

   ```python
   def breadthFirstValues(root):
     '''Iterative Approach'''
     from collections import deque
     q = deque([root])
     while q:
       cur = q.popleft()
       print(cur.val, end=",")
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

4. [**Depth First List**] Given the root of a binary tree, write a function to return a list of all values in the tree using a depth first search approach (dfs).

   ```python
   def depthFirstValues(root):
    '''Iterative Approach'''
     if not root: return []
     res = []
     s = [root]
     while s:
       cur = s.pop()
       res.append(cur.val)
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
     return res
   ```

   ```python
   def depthFirstValues(root):
    '''Recursieve Approach'''
    if not root: return []
    return [root.val, *depthFirstValues(root.left), *depthFirstValues(root.right)]
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

5. [**Breadth First List**] Given the root of a binary tree, write a function to return a list of all values in the tree using a depth first search approach (dfs).

   ```python
   def breadthFirstValues(root):
    '''Iterative Approach'''
     if not root: return []
     res = []
     q = [root]
     while q:
       cur = q.pop(0)
       res.append(cur.val)
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return res
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n^2)
   ```

6. [[**Bottom Left Value**](https://leetcode.com/problems/find-bottom-left-tree-value/)] Given the root of a binary tree, write a function to return the leftmost value in the last row of the tree.

   `Iterative Approach (BFS)`

   ```python
   def findBottomLeftValue(root):
     if not root: return
     q = [root]
     while q:
       cur = q.pop(0)
       if cur.right: q.append(cur.right)
       if cur.left: q.append(cur.left)
     return cur.val
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

7. [**Bottom Right Value**] Given the root of a binary tree, write a function to return the rightmost value in the last row of the tree.

   `Iterative Approach (BFS)`

   ```python
   def findBottomRightValue(root):
    from collections import deque
     if not root: return
     q = deque([root])
     while q:
       cur = q.popleft()
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return cur.val
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

8. [**Tree Sum**] Given the root of a binary tree that contains all number values, write a function to return the sum of all the values in the tree.

   ```python
   def treeSum(root):
    '''Iterative DFS Approach'''
     if not root: return 0
     res = 0
     s = [root]
     while s:
       cur = s.pop()
       res += cur.val
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
     return res
   ```

   ```python
   def treeSum(root):
    '''Recursieve DFS Approach'''
    if not root: return 0
    return root.val + treeSum(root.left) + treeSum(root.right)
   ```

   ```python
   def treeSum(root):
    '''Recursieve DFS Approach'''
    def treeValues(node):
      if not root: return []
      return [root.val, *treeValues(node.left), *treeValues(node.right)]
    return sum(treeValues(root))
   ```

   ```python
   def treeSum(root):
    '''Iterative BFS Approach'''
     if not root: return 0
     res = 0
     q = [root]
     while q:
       cur = q.pop(0)
       res += cur.val
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return res
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

9. [**Find Value**] Given the root of a binary tree and a target value, write a function to return a boolean indicating whether or not the target value is in the tree.

   ```python
   def findTarget(root, target):
    '''Iterative DFS Approach'''
     if not root: return False
     s = [root]
     while s:
       cur = s.pop()
       if cur.val == target: return True
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
     return False
   ```

   ```python
   def findTarget(root, target):
    '''Recursieve DFS Approach'''
    if not root: return False
    if root.val == target: return True
    return findTarget(root.left, target) or findTarget(root.right, target)
   ```

   ```python
   def findTarget(root, target):
    '''Recursieve DFS Approach'''
    def treeValues(node):
      if not root: return []
      return [root.val, *treeValues(node.left), *treeValues(node.right)]
    return (target in treeValues(root))
   ```

   ```python
   def findTarget(root, target):
    '''Iterative BFS Approach'''
     if not root: return False
     q = [root]
     while q:
       cur = q.pop(0)
       if cur.val == target: return True
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return False
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

10. [**Same Tree**] Given the roots of two binary trees `p` and `q`, write a function that returns a boolean indicating whether or not the trees are the same.  

   ```python
   def sameTree(p, q):
    if not p or not q: return p == q
    left_same = self.isSameTree(p.left, q.left)
    right_same = self.isSameTree(p.right, q.right)
    return p.val==q.val and left_same and right_same
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

11. [**Min Value**] Given the root of a binary tree containing all numerical values, write a function to return the minimum value in the tree. Assume an non-empty tree.

    ```python
    def findMinValue(root):
     '''Iterative DFS Approach'''
     min_val = float("inf")
     s = [root]
     while s:
       cur = s.pop()
       min_val = min(cur.val, min_val)
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
     return min_val
    ```

    ```python
    def findMinValue(root):
     '''Recursieve DFS Approach'''
     if not root: return float("inf")
     return min(root.val, findMinValue(root.left), findMinValue(root.rightt))
    ```

    ```python
    def findMinValue(root):
     '''Recursieve DFS Approach'''
     def treeValues(node):
       if not root: return []
       return [root.val, *treeValues(node.left), *treeValues(node.right)]
     return min(treeValues(root))
    ```

    ```python
    def findMinValue(root):
     '''Iterative BFS optimal Approach'''
     from collection import deque
     if not root: return
     min_val = float("inf")
     q = [root]
     while q:
       cur = q.popleft()
       min_val = min(cur.val, min_val)
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return min_val
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

12. [**Max Value**] Given the root of a binary tree containing all numerical values, write a function to return the maximum value in the tree. Assume an non-empty tree.

    ```python
    def findMaxValue(root):
     '''Recursieve DFS Approach'''
     if not root: return float("-inf")
     return max(root.val, findMaxValue(root.left), findMaxValue(root.rightt))
    ```

    ```python
    def findMaxValue(root):
     '''Iterative BFS optimal Approach'''
     from collection import deque
     if not root: return
     max_val = float("-inf")
     q = [root]
     while q:
       cur = q.popleft()
       max_val = max(cur.val, min_val)
       if cur.left: q.append(cur.left)
       if cur.right: q.append(cur.right)
     return max_val
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

13. [**Min Path Sum**] Given the root of a binary tree containing all numerical values, write a function to return the minimum sum of any root to leaf path within the tree. Assume an non-empty tree.

    ```python
    def minPathSum(root):
     '''Recursieve DFS Approach'''
     if not root: return float("inf")
     if not root.left and not root.right: return root.val
     return root.val + min(minPathSum(root.left), minPathSum(root.rightt))
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

14. [**Max Path Sum**] Given the root of a binary tree containing all numerical values, write a function to return the maximum sum of any root to leaf path within the tree. Assume an non-empty tree.

    ```python
    def maxPathSum(root):
     '''Recursieve DFS Approach'''
     if not root: return float("-inf")
     if not root.left and not root.right: return root.val
     return root.val + max(maxPathSum(root.left), maxPathSum(root.rightt))
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

15. [**Min Path**] Given the root of a binary tree containing all numerical values, write a function to return the minimum path from the root to any leaf within the tree. Assume an non-empty tree.

    ```python
    def minPath(root):
     '''Recursieve DFS Approach'''
     if not root: return [float("inf")]
     if not root.left and not root.right: return [root.val]
     left_path, right_path = minPath(root.left), minPath(root.right)
     if sum(left_path) < sum(right_path):
      return [root.val, *left_path]
     else:
      return [root.val, *right_path]
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

16. [**Max Path**] Given the root of a binary tree containing all numerical values, write a function to return the maximum path from the root to any leaf within the tree. Assume an non-empty tree.

    ```python
    def maxPath(root):
     '''Recursieve DFS Approach'''
     if not root: return [float("-inf")]
     if not root.left and not root.right: return [root.val]
     left_path, right_path = maxPath(root.left), maxPath(root.right)
     if sum(left_path) > sum(right_path):
      return [root.val, *left_path]
     else:
      return [root.val, *right_path]
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

17. [**Path Finder**] Given the root of a binary tree and a target value, write a function to return an array representing the path to the target value. Assume an non-empty tree containing unique values.

    ```python
    def pathFinder(root, target):
     '''Recursieve DFS Approach'''
     if not root: return None
     if root.val == target: return [root.val]
     left_path, right_path = pathFinder(root.left, target), pathFinder(root.right, target)
     if left_path: return [root.val, *left_path]
     if right_path: return [root.val, *right_path]
     return None
    ```

    ```
    n is the number of nodes
    Time: O(n^2)
    Space: O(n)
    ```

    ```python
    def pathFinder(root, target):
     '''Recursieve DFS Approach'''
     def helper_pathFinder(root, target):
      if not root: return None
      if root.val == target: return [root.val]
      left_path, right_path = helper_pathFinder(root.left, target), helper_pathFinder(root.right, target)
      if left_path:
        left_path.append(root.val)
        return left_path
      if right_path:
        right_path.append(root.val)
        return right_path
      return None

     path = helper_pathFinder(root, target)
     return path[::-1] if path else None

    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

18. [**Lowest Common Ancestor**] [[**Leetcode 236**](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)] Given the root of a binary tree and a target value, write a function to return an array representing the path to the target value. Assume an non-empty tree containing unique values.

    ```python
    def lowestCommonAncestor(root, val1, val2):
      path1 = pathFinder(root, val1)
      path2 = set(pathFinder(root, val2))
      for val in path1:
        if val in path2:
          return val

    def pathFinder(root, target):
      if not root: return None
      if root.val == target: return [root.val]

      left_path = pathFinder(root.left, target)
      if left_path:
        left_path.append(root.val)
        return left_path

      right_path = pathFinder(root.right, target)
      if right_path:
        right_path.append(root.val)
        return right_path
      return None
    ```

    ```python
    def lowestCommonAncestor(root, p, q):
      if not root: return None
      if root.val == p or root.val == q: return root.val

      left = lowestCommonAncestor(root.left, p, q)
      right = lowestCommonAncestor(root.right, p, q)

      if (not left and not right ): return None
      if (left and right): return root.val

      if left: return left
      else: return right
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

19. [[**Path Sum**](https://leetcode.com/problems/path-sum/)] Given the root of a binary tree and an integer target value, write a function to return a boolean indicating wheater or not theres a root-to-lead path that adds up to the target sum.

    ```python
    def hasPathSum(root, target):
      '''Recursive Approach'''
      if not root: return False
      rem = root.val - target
      if not root.left and not root.right and rem == 0: return True
      return self.hasPathSum(root.left, rem) or self.hasPathSum(root.right, rem)
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

20. [[**Invert Tree**](https://leetcode.com/problems/invert-binary-tree/)] Given the root of a binary tree, write a function to invert the tree and return it's root.

    ```python
    def invertTree(root):
      if not root: return None
      root.left, root.right = invertTree(root.right), invertTree(root.left)
      return root
    ```
    ```python
    def invertTree(root):
      if not root: return None
      s = [root]
      while s:
        cur = s.pop()
        cur.left, cur.right = cur.right, cur.left
        if cur.left: s.append(cur.left)
        if cur.right: s.append(cur.right)
      return root
    ```
    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

21. [[**Symmetric Tree**](https://leetcode.com/problems/symmetric-tree/description/)] Given the root of a binary tree, write a function to return a boolean indicating whether or not the tree is symmetric.

    ```python
    def isSymmetric(root):
      if not root: return True
      s = [(root.left, root.right)]
      while s:
          left, right = s.pop()
          if not left and not right: continue
          if not left or not right or (left.val != right.val): return False
          s.append((left.left, right.right))
          s.append((left.right, right.left))
      return True
    ```
    ```python
    def isSymmetric(root):
      return checkSymmetry(root, root)

    def checkSymmetry(root1, root2):
      if not root1 and not root2: return True
      if not root1 or not root2: return False
      return (root1.val == root2.val) and checkSymmetry(root1.left, root2.right) and checkSymmetry(root1.right, root2.left)
    ```
    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

22. [**Merge Two Trees**] [[**Leetcode 617**](https://leetcode.com/problems/merge-two-binary-trees/)] Given the respective roots of two binary trees, Imagine putting both trees on top of each other, some nodes overlap and others don't. Write a function to merge both trees based on the merge rules that overlapping nodes get added otherwise, non-Null nodes will be used in resulting tree.

    ```python
    def mergeTrees(root1, root2):
      if not root1 and not root2: return None
      v1 = root1.val if root1 else 0
      v2 = root2.val if root2 else 0
      root = TreeNode(v1 + v2)
      root.left = mergeTrees(root1.left if root1 else None, root2.left if root2 else None)
      root.right = mergeTrees(root1.right if root1 else None, root2.right if root2 else None)
      return root
    ```

    ```python
    def invertTree(root):
      if not root: return None
      s = [root]
      while s:
        cur = s.pop()
        cur.left, cur.right = cur.right, cur.left
        if cur.left: s.append(cur.left)
        if cur.right: s.append(cur.right)
      return root
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

23. [**Count Value**] Given the root of a binary tree and a target value, write a function to return the number of times the target occurs in the tree.

    `Iterative Approach (DFS)`

    ```python
    def countValue(root, target):
      if not root: return 0
      count = 0
      s = [root]
      while s:
        cur = s.pop()
        if cur.val == target: count += 1
        if cur.left: s.append(cur.left)
        if cur.right: s.append(cur.right)
      return count
    ```

    `Recursive Approach (DFS)`

    ```python
    def countValue(root, target):
      if not root: return 0
      match = 1 if root.val == target else 0
      return match + countValue(root.left, target) + countValue(root.right, target)
    ```

    `Iterative Approach (BFS)`

    ```python
    def countValue(root, target):
      from collections import deque
      if not root: return 0
      count = 0
      q = deque([root])
      while q:
        cur = q.popleft()
        if cur.val == target: count += 1
        if cur.left: q.append(cur.left)
        if cur.right: q.append(cur.right)
      return count
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

24. [**Tree Height**] Given the root of a binary, write a function to return a number representing the height of the tree. An empty tree should return `-1` and a singleton tree should return `0`.

    ```python
    def treeHeight(root):
      if not root: return -1
      return 1 + max(treeHeight(root.left), treeHeight(root.right))
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

25. [**Tree Diameter**] [[**Leetcode 543**](https://leetcode.com/problems/diameter-of-binary-tree/)] Given the root of a binary, write a function to return the length of the diameter of the tree. The diameter is the length of the longest path between any two nodes measured by the number of edges.

    ```python
    def dfs(root):
      if not root: return (0, 0)
      left_height, left_diameter = dfs(root.left)
      right_height, right_diameter = dfs(root.right)

      height = 1 + max(left_height, right_height)
      diameter = max(left_diameter, right_diameter, left_height + right_height)
      return (height, diameter)

    def diameterOfTree(root):
      height, diameter = dfs(root)
      return diameter
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

26. [**All Paths**] Given the root of a binary tree, write a function to return a 2-D list containing all possible root-to-leaf paths in correct order.

    ```python
    def allPaths(root):
      if not root: return []
      if not root.left and not root.right: return [[root.val]]

      paths = []
      left_paths = allPaths(root.left)
      for sub_path in left_paths:
        paths.append([root.val, *sub_path])

      right_paths = allPaths(root.right)
      for sub_path in right_paths:
        paths.append([root.val, *sub_path])

      return paths
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

27. [[**Binary Tree Paths**](https://leetcode.com/problems/binary-tree-paths/)] Given the root of a binary tree, write a function to return a 2-D list containing all possible root-to-leaf paths in correct order as a string.

    ```python
    def binaryTreePaths(root):
      if not root: return []
      if not root.left and not root.right: return [str(root.val)]

      paths = []
      left_paths = binaryTreePaths(root.left)
      for sub_path in left_paths:
        paths.append(f"{root.val}->{sub_path}")

      right_paths = binaryTreePaths(root.right)
      for sub_path in right_paths:
        paths.append(f"{root.val}->{sub_path}")

      return paths
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

28. [**Tree Levels**] Given the root of a binary tree, write a function to return a 2-D list where each sublist is a level of the tree.

    ```python
    def treeLevels(root):
      if not root: return []
      levels = []
      s = [(root, 0)]
      while s:
        (cur, cur_level) = s.pop()
        if len(levels) == cur_level: levels.append([cur.val])
        else: levels[cur_level].append(cur.val)
        if cur.right: s.append((cur.right, cur_level+1))
        if cur.left: s.append((cur.left, cur_level+1))
      return levels
    ```

    ```python
    def treeLevels(root):
      def fillLevels(root, levels, cur_level):
        if not root: return None
        if len(levels) == cur_level: levels.append([root.val])
        else: levels[cur_level].append(root.val)
        fillLevels(root.left, levels, cur_level+1)
        fillLevels(root.right, levels, cur_level+1)
      levels = []
      fillLevels(root, levels, 0)
      return levels
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

29. [**Tree Levels II**] Given the root of a binary tree, write a function to return a dictionary/ hash map where each list in the dictionary is a level of the tree.

    ```python
    def treeLevels(root):
      if not root: return {}
      levels = {}
      s = [(root, 0)]
      while s:
        (cur, cur_level) = s.pop()
        if len(levels) == cur_level: levels[cur_level] = [cur.val]
        else: levels[cur_level].append(cur.val)
        if cur.right: s.append((cur.right, cur_level+1))
        if cur.left: s.append((cur.left, cur_level+1))
      return levels
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

30. [**Level Averages**] Given the root of a binary tree, write a function to return a list containing the average of each level of the tree.

    ```python
    def levelAverages(root):
      def fillLevels(root, levels, cur_level):
        if not root: return None
        if len(levels) == cur_level: levels.append([root.val])
        else: levels[cur_level].append(root.val)
        fillLevels(root.left, levels, cur_level+1)
        fillLevels(root.right, levels, cur_level+1)
      levels = []
      fillLevels(root, levels, 0)
      return [sum(level)/len(level) for level in levels]
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

31. [**Lefty Nodes**] Given the root of a binary tree, write a function to return a list containing all the leftmost nodes on every level of the tree.

    ```python
    def leftyNodes(root):
      levels = treeLevels(root)
      return [level[0] for level in levels]

    def treeLevels(root):
      def fillLevels(root, levels, cur_level):
        if not root: return None
        if len(levels) == cur_level: levels.append([root.val])
        else: levels[cur_level].append(root.val)
        fillLevels(root.left, levels, cur_level+1)
        fillLevels(root.right, levels, cur_level+1)
      levels = []
      fillLevels(root, levels, 0)
      return levels
    ```

    ```python
    def leftyNodes(root):
      values = []
      dft(root, 0, values)
      return values

    def dft(root, level, values):
      if not root: return None
      if len(values) == level: values.append(root.val)
      dft(root.left, level+1, values)
      dft(root.right, level+1, values)
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

32. [**Righty Nodes**] Given the root of a binary tree, write a function to return a list containing all the rightmost nodes on every level of the tree.

    ```python
    def leftyNodes(root):
      levels = treeLevels(root)
      return [level[-1] for level in levels]

    def treeLevels(root):
      def fillLevels(root, levels, cur_level):
        if not root: return None
        if len(levels) == cur_level: levels.append([root.val])
        else: levels[cur_level].append(root.val)
        fillLevels(root.left, levels, cur_level+1)
        fillLevels(root.right, levels, cur_level+1)
      levels = []
      fillLevels(root, levels, 0)
      return levels
    ```
    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

33. [**Leaf Lists**] Given the root of a binary tree, write a function to return a list containing the values of all leaf nodes in left-to-right order.

    ```python
    def leafList(root):
      if not root: return []
      leafs = []
      s = [root]
      while s:
        cur = s.pop()
        if not cur.right and not cur.left: leafs.append(cur.val)
        if cur.right: s.append(cur.right)
        if cur.left: s.append(cur.left)
      return leafs
    ```

    ```python
    def leafList(root):
      if not root: return []
      if not root.left and not root.right: return [root.val]
      return [*leafList(root.left), *leafList(root.right)]
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

34. [**Sum of Left Leaves**] [[**Leetcode 404**](https://leetcode.com/problems/sum-of-left-leaves/)] Given the root of a binary tree, write a function to return the sum of all left leaves.

    ```python
    def sumOfLeftLeaves(root):
      if not root: return 0
      if root.left and not root.left.left and not root.left.right:
        return root.left.val + self.sumOfLeftLeaves(root.right)
      else:
        return self.sumOfLeftLeaves(root.left) + self.sumOfLeftLeaves(root.right)
    ```
    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

---

### Binary Search Trees

1. [**Search BST**] Given the root of a binary search tree and a target value, write a function that returns a boolean indicating whether or not the target is found in the BST.

   ```python
   def searchBST(root, target):
    if not root: return False
    if root.val == target: return True
    if root.val < target: return self.searchBST(root.right, target)
    else: return self.searchBST(root.left, target)
   ```
   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(1)
   ```

2. [**Search BST II**] [[**leetcode 700**](https://leetcode.com/problems/search-in-a-binary-search-tree/)] Given the root of a binary search tree and a target value, write a function to find the node in the BST whose value equals the target value and return the subtree rooted at that node. If no such node exists, return `None`.

   ```python
   def searchBST(root, target):
    if not root: return None
    if root.val == target: return root
    if root.val < target: return searchBST(root.right, target)
    else: return searchBST(root.left, target)
   ```
   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(1)
   ```

3. [**Add Node**] [[**leetcode 701**](https://leetcode.com/problems/insert-into-a-binary-search-tree/)] Given the root of a binary search tree and a value to insert, write a function to insert the node to the BST and return the root node of the BST.

   ```python
   def addNode(root, value):
     if not root: return Node(value)
     if root.val < value: root.right = addNode(root.right, value)
     elif root.val > value: root.left = addNode(root.left, value)
     return root
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(1)
   ```

4. [**Delete Node**] [[**leetcode 450**](https://leetcode.com/problems/delete-node-in-a-bst/)] Given the root of a binary search tree and a value to delete, write a function to delete the node of the BST and return the root node.

   ```python
   def findMinNode(root):
    cur = root
    while cur.left:
      cur = cur.left
    return cur

   def deleteNode(root, value):
    if not root: return None
    if root.val > value: root.left = deleteNode(root.left, value)
    elif root.val < value: root.right = deleteNode(root.right, value)
    else:
      if not root.left:
        temp = root.right
        root = None
        return temp
      else not root.right:
        temp = root.left
        root = None
        return temp
      else:
        temp = findMinNode(root.right)
        root.val = temp.val
        root.right = deleteNode(root.right, temp.val)
    return root
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(1)
   ```

5. [[**Lowest Common Ancestor**](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)] Given the root of a binary search tree and two nodes, write a function to return the lowest common ancestor of both nodes.

   ```python
   def lowestCommonAncestor(root, p, q):
     if p.val < root.val and q.val < root.val: return lowestCommonAncestor(root.left, p, q)
     elif p.val > root.val and q.val > root.val: return lowestCommonAncestor(root.right, p, q)
     else: return root
   ```

   ```python
   def lowestCommonAncestor(root, p, q):
    while (root.val - p.val) * (root.val - q.val) > 0:
      root = (root.left, root.right)[p.val > root.val]
    return root
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(1)
   ```

6. [**Validate BST**] [[**leetcode 98**](https://leetcode.com/problems/validate-binary-search-tree/)] Given the root of a binary search tree, write a function to return a boolean representing if it's a valid binary search tree (BST).

   ```python
   def isValidBST(root):
    def validate(node, left, right):
      if not node: return True
      if not (left < node.val < right): return False
      return (validate(node.left, left, node.val) and validate(node.right, node.val, right))
    return valid(root, float("-inf"), float("inf"))
   ```
   ```python
   def isValidBST(root):
    if not root: return True
    s = [(root, float("-inf"), float("inf"))]
    while s:
      cur, left, right = s.pop()
      if not (left < cur.val < right): return False
      if cur.left: s.append((cur.left, left, cur.val))
      if cur.right: s.append((cur.right, cur.val, right))
    return True
   ```
   ```python
   def isValidBST(root):
    if not root: return True
    q = [(root, float("-inf"), float("inf"))]
    while q:
      cur, left, right = q.pop(0)
      if not (left < cur.val < right): return False
      if cur.left: s.append((cur.left, left, cur.val))
      if cur.right: s.append((cur.right, cur.val, right))
    return True
   ```
   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(n)
   ```

7. [**Sorted Array to BST**] [[**leetcode 108**](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)] Given an integer array with each element sorted in ascending order, write a function that converts it to a height-balanced BST and returns the root.

   ```python
   def sortedArrayToBST(nums):
    if not nums: return None

    def helper(l, r):
      if l > r: return None
      m = (l+r)//2
      root = TreeNode(nums[m])
      root.left = helper(l, m-1)
      root.right = helper(m+1, r)
      return root

    return helper(0, len(nums)-1)
   ```
   ```python
   def sortedArrayToBST(nums):
    if not nums: return None
    total_nums = len(nums)
    mid = total_nums // 2
    return TreeNode(nums[mid], sortedArrayToBST(nums[:mid]), sortedArrayToBST(nums[mid+1:]))
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(n)
   ```


8. [**Sorted List to BST**] [[**leetcode 109**](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)] Given the head of a singly linked list with each element sorted in ascending order, write a function that converts it to a height-balanced BST and returns the root.

   ```python
   def sortedListToBST(head):
    if not head: return None
    nums = []
    while head:
      nums.append(head.val)
      head = head.next

    def helper(l, r):
      if l > r: return None
      m = (l+r)//2
      root = TreeNode(nums[m])
      root.left = helper(l, m-1)
      root.right = helper(m+1, r)
      return root

    return helper(0, len(nums)-1)
   ```
   ```python
   def sortedListToBST(head):
    if not head: return None
    if not head.next: return TreeNode(head.val)
    slow = fast = head
    while fast and fast.next:
      mid = slow
      fast = fast.next.next
      slow = slow.next
    mid.next = None
    root = TreeNode(slow.val)
    root.left = sortedListToBST2(head)
    root.right = sortedListToBST2(slow.next)
    return root
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(n)
   ```

9. [**Closest Value in BST**] Given the root of a BST and a target value, write a function to return the closest value to the target value. You can assume that there will be only 1 closest value to the target.

   ```python
   def findClosestValueInBst(root, target):
    closest = float("inf")
    while root:
      closest = root.value if abs(root.value-target) < abs(closest-target) else closest
      if root.value < target: root = root.right
      else: root = root.left
    return closest
   ```
   ```python
   def findClosestValueInBst(root, target):
    if not root: return closest
    if not closest or abs(root.value-target) < abs(closest-target): closest = root.value
    if root.value > target: return findClosestValueInBst(root.left, target, closest)
    elif root.value < target: return findClosestValueInBst(root.right, target, closest)
    return closest
   ```

   ```
   n is the number of nodes
   Time: O(log(n))
   Space: O(n)
   ```


---

### Graphs

1. [**Build Graph**] Given a graph as an edge list, write a function to convert/ build it into an adjacency list.

   ```python
     '''
        edges list = [
          ['i','j'],
          ['k','i'],
          ['m','k'],
          ['k','l'],
          ['o','n']
                ]

        adjancecy list = {
          'i': ['j', 'k'],
          'j': ['i'],
          'k': ['i', 'm', 'l'],
          'm': ['k'],
          'l': ['k'],
          'o': ['n'],
          'n': ['o']
        }
     '''
   ```

   ```python
   def buildGraph(edges):
    graph = {}
    for edge in edges:
      (a,b) = edge
      if a not in graph: graph[a] = []
      if b not in graph: graph[b] = []
      graph[a].append(b)
      graph[b].append(a)
    return graph
   ```

   ```
     n is the number of nodes.
     Time: O(n)
     Space: O(n)
   ```

2. [**Depth First Values**] Given a graph as a dictionary/adjacency list and a source node `a`, write a function to print all values in the graph in a depth first search (DFS) manner.

   ```python
   def depthFirstTraversal(graph, src):
    s = [src]
    while s:
      cur = s.pop()
      print(cur, end=", ")
      for n in graph[cur]:
        s.append(n)
   ```

   ```python
   def depthFirstTraversal(graph, src):
    print(cur, end=", ")
    for n in graph[src]:
      depthFirstTraversal(graph, n)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

3. [**Breadth First Values**] Given a graph as a dictionary/adjacency list and a source node `a`, write a function to print all values in the graph in a breadth first search (BFS) manner.

   ```python
   def breadthFirstTraversal(graph, src):
    q = [src]
    while q:
      cur = q.pop(0)
      print(cur, end=", ")
      for n in graph[cur]:
        q.append(n)
   ```

   ```
   n is the number of nodes
   Time: O(n^2)
   Space: O(n)
   ```

   ```python
   def breadthFirstTraversal(graph, src):
    from collections import deque
    q = deque([src])
    while q:
      cur = q.popleft()
      print(cur, end=", ")
      for n in graph[cur]:
        q.append(n)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

4. [**Has Path**] Given a directed acyclic graph (DAG) as a dictionary/adjacency list, a source node `src`, and a destination node `dst`. Write a function that returns a boolean indicating whether or not there is a path from `src` to `dst`.

   ```python
   def hasPath(graph, src, dst):
    s = [src]
    while s:
      cur = s.pop()
      if cur == dst: return True
      for n in graph[cur]: s.append(n)
      return False
   ```

   ```python
   def hasPath(graph, src, dst):
    if src == dst: return True
    for n in graph[src]:
      if hasPath(graph, n, dst): return True
    return False
   ```

   ```python
   def hasPath(graph, src, dst):
    q = [src]
    while q:
      cur = q.pop(0)
      if cur == dst: return True
      for n in graph[cur]: q.append(n)
      return False
   ```

   ```python
   def breadthFirstTraversal(graph, src, dst):
    from collections import deque
    q = deque([src])
    while q:
      cur = q.popleft()
      if cur == dst: return True
      for n in graph[cur]: q.append(n)
      return False
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

5. [**Has Path**] [[**Leetcode 1971**](https://leetcode.com/problems/find-if-path-exists-in-graph/)] Given a bi-directional possibly cyclic graph as a an edge list, a source node `src`, and a destination node `dst`. Write a function that returns a boolean indicating whether or not there is a path from `src` to `dst`.

   ```python
   def buildGraph(edges):
    graph = {}
    for (a,b) in edges:
      if a not in graph: graph[a] = []
      if b not in graph: graph[b] = []
      graph[a].append(b)
      graph[b].append(a)
    return graph

   def hasPath(graph, src, dst, visited=set()):
    s, visited = [src], set()
    while s:
      cur = s.pop()
      visited.add(cur)
      if cur == dst: return True
      for n in graph[cur]:
        if n not in visited:
          s.append(n)
    return False

   def undirectedHasPath(edges, nodeA, nodeB):
    graph = buildGraph(edges)
    return hasPath(graph, nodeA, nodeB)
   ```

   ```python
   def buildGraph(edges):
    graph = {}
    for (a,b) in edges:
      if a not in graph: graph[a] = []
      if b not in graph: graph[b] = []
      graph[a].append(b)
      graph[b].append(a)
    return graph

   def hasPath(graph, src, dst, visited=set()):
    if src in visited: return False
    if src == dst: return True
    visited.add(src)
    for n in graph[src]:
      if hasPath(graph, n, dst, visited): return True
    return False

   def undirectedHasPath(edges, nodeA, nodeB):
    graph = buildGraph(edges)
    return hasPath(graph, nodeA, nodeB)
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

6. [**Connected Components**] Given an undirected graph as a dictionary/adjacency list, write a function that returns the number of connected components within the graph.

   ```python
   def explore(graph, node, visited=set()):
    if node in visited: return False
    visited.add(node)
    for n in graph[node]:
      explore(graph, n, visited)
    return True

   def connectedComponents(graph):
    count = 0
    for n in graph:
      if explore(graph, n):
        count += 1
    return count
   ```

   ```python
   def explore(graph, node, visited=set()):
    if node in visited: return 0
    visited.add(node)
    for n in graph[node]:
      explore(graph, n, visited)
    return 1

   def connectedComponents(graph):
    count = 0
    for n in graph:
      count += explore(graph, n)
    return count
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

7. [**Connected Components**] [[**Leetcode 323**](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)] Given an undirected graph as an edge list, write a function that returns the number of connected components within the graph.

   ```python
   def buildGraph(edges):
    graph = {}
    for n in range(0, n): graph[n] = []
    for (a,b) in edges:
      graph[a].append(b)
      graph[b].append(a)
    return graph

   def explore(graph, node, visited=set()):
    if node in visited: return 0
    visited.add(node)
    for n in graph[node]:
      explore(graph, n, visited)
    return 1

   def connectedComponents(edges):
    graph = buildGraph(edges)
    count = 0
    for n in graph:
      count += explore(graph, n)
    return count
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

8. [**Largest Component**] Given an undirected graph as a dictionary/adjacency list, write a function that returns the size of the largest connected component within the graph.

   ```python
   def explore(graph, node, visited=set()):
    if node in visited: return 0
    visited.add(node)
    size = 1
    for n in graph[node]:
      size += explore(graph, n, visited)
    return size

   def largestComponent(graph):
    largest = 0
    for n in graph:
      size = explore(graph, n)
      largest = max(largest, size)
    return largest
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

9. [**Smallest Component**] Given an undirected graph as a dictionary/adjacency list, write a function that returns the size of the smallest connected component within the graph.

   ```python
   def explore(graph, node, visited=set()):
    if node in visited: return 0
    visited.add(node)
    size = 1
    for n in graph[node]:
      size += explore(graph, n, visited)
    return size

   def smallestComponent(graph):
    smallest = float("inf")
    for n in graph:
      size = explore(graph, n)
      if size: smallest = min(smallest, size)
    return smallest
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

10. [**Shortest Path**] Given an undirected graph as an edge list and two nodes `(nodeA, nodeB)`, write a function that returns the length of the shortest path between those nodes. if there's no path, return `-1`.

    ```python
    def buildGraph(edges):
      graph = {}
      for (a,b) in edges:
        if a not in graph: graph[a] = []
        if b not in graph: graph[b] = []
        graph[a].append(b)
        graph[b].append(a)
      return graph

    def shortestPath(edges, nodeA, nodeB):
      graph = buildGraph(edges)
      q = [(nodeA, 0)]
      visited = set(nodeA)
      while q:
        cur, dist = q.pop(0)
        if cur == nodeB: return dist
        for n in graph[cur]:
          if n not in visited:
            visited.add(n)
            q.append((n, dist+1))
      return -1
    ```

    ```python
    def buildGraph(edges):
      graph = {}
      for (a,b) in edges:
        if a not in graph: graph[a] = []
        if b not in graph: graph[b] = []
        graph[a].append(b)
        graph[b].append(a)
      return graph

    def shortestPath(edges, nodeA, nodeB):
      graph = buildGraph(edges)
      s = [(nodeA, 0)]
      visited = set(nodeA)
      min_dist = float("inf")
      while s:
        cur, dist = s.pop()
        if cur == nodeB:
          min_dist = min(min_dist, dist)
          return min_dist
        for n in graph[cur]:
          if n not in visited:
            visited.add(n)
            s.append((n, dist+1))
      return -1
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

11. [**Battleships in a Board**] [[**Leetcode 419**](https://leetcode.com/problems/battleships-in-a-board/)] Given a grid containing `X` and `.` to represent a battleship or empty cell respectively, write a function to return the number of battleships on the grid.

    ```python
    def countBattleships(board):
      count = 0
      for i in range(len(board)):
        for j in range(len(board[i])):
          count += explore(board, i, j)
      return count

    def explore(self, board, i, j):
      rowInbounds = 0 <= i < len(board)
      colInbounds = 0 <= j < len(board[0])
      if not rowInbounds or not colInbounds or board[i][j] == ".": return 0

      board[i][j] = "."
      explore(board, i+1, j)
      explore(board, i-1, j)
      explore(board, i, j+1)
      explore(board, i, j-1)
      return 1
    ```
    ```
    n is the length of the board
    m ins the width of the board
    Time: O(n*m)
    Space: O(n)
    ```


12. [**Number of Islands**] [[**Leetcode 200**](https://leetcode.com/problems/number-of-islands/)] Given a grid containing Ws and Ls where W represents water and L represents land. Write a function to return the number of islands on the grid.

    ```python
    def explore(grid, r, c, visited=set()):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[r])
      if (not rowInbounds or not colInbounds): return False

      if grid[r][c] == 'W': return False

      pos = str(r) + ',' + str(c)
      if pos in visited: return False
      visited.add(pos)

      explore(grid, r-1, c, visited)
      explore(grid, r+1, c, visited)
      explore(grid, r, c-1, visited)
      explore(grid, r, c+1, visited)
      return True

    def islandCount(grid):
      count = 0
      for r in range(len(grid)):
        for c in range(len(grid[0])):
          if explore(grid, r, c):
            count += 1
      return count
    ```

    ```python
    def explore(grid, r, c):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[r])
      if (not rowInbounds or not colInbounds or grid[r][c]=='W'): return 0

      grid[r][c] = 'W'

      explore(grid, r-1, c)
      explore(grid, r+1, c)
      explore(grid, r, c-1)
      explore(grid, r, c+1)
      return 1

    def islandCount(grid):
      count = 0
      for r in range(len(grid)):
        for c in range(len(grid[r])):
          if grid[r][c] == 'L':
            count += explore(grid, r, c)
      return count
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

13. [**Max Area of Island**] [[**Leetcode 695**](https://leetcode.com/problems/number-of-islands/)] Given a grid containing Ws and Ls where W represents water and L represents land. Write a function to return the size of the largest island.

    ```python
    def explore(grid, r, c, visited=set()):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[0])
      if (not rowInbounds or not colInbounds or grid[r][c] == 'W'): return 0

      pos = (r,c)
      if pos in visited: return 0
      visited.add(pos)

      size = 1
      size += explore(grid, r-1, c, visited)
      size += explore(grid, r+1, c, visited)
      size += explore(grid, r, c-1, visited)
      size += explore(grid, r, c+1, visited)
      return size

    def maxIsland(grid):
      max_size = 0
      for r in range(len(grid)):
        for c in range(len(grid[0])):
          size = explore(grid, r, c)
          max_size = max(max_size, size)
      return max_size
    ```

    ```python
    def explore(grid, r, c):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[0])
      if (not rowInbounds or not colInbounds or grid[r][c] == 'W'): return 0

      grid[r][c] = 'W'

      size = 1
      size += explore(grid, r-1, c)
      size += explore(grid, r+1, c)
      size += explore(grid, r, c-1)
      size += explore(grid, r, c+1)
      return size

    def maxIsland(grid):
      max_size = 0
      for r in range(len(grid)):
        for c in range(len(grid[0])):
          if grid[r][c] == 'L':
            max_size = max(max_size, explore(grid, r, c))
      return max_size
    ```

    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```

14. [**Min Area of Island**] Given a grid containing Ws and Ls where W represents water and L represents land. Write a function to return the size of the smallest island.

    ```python
    def explore(grid, r, c, visited=set()):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[0])
      if (not rowInbounds or not colInbounds or grid[r][c] == 'W'): return 0

      pos = (r,c)
      if pos in visited: return 0
      visited.add(pos)

      size = 1
      size += explore(grid, r-1, c, visited)
      size += explore(grid, r+1, c, visited)
      size += explore(grid, r, c-1, visited)
      size += explore(grid, r, c+1, visited)
      return size

    def minIsland(grid):
      min_size = float('inf')
      for r in range(len(grid)):
        for c in range(len(grid[0])):
          size = explore(grid, r, c)
          if min_size > 0: min_size = min(min_size, size)
      return min_size
    ```

    ```python
    def explore(grid, r, c):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[0])
      if (not rowInbounds or not colInbounds or grid[r][c] == 'W'): return 0

      grid[r][c] = 'W'

      size = 1
      size += explore(grid, r-1, c)
      size += explore(grid, r+1, c)
      size += explore(grid, r, c-1)
      size += explore(grid, r, c+1)
      return size

    def minIsland(grid):
      min_size = float('inf')
      for r in range(len(grid)):
        for c in range(len(grid[r])):
          if grid[r][c] == 'L':
            min_size = min(min_size, explore(grid, r, c))
      return min_size
    ```

    ```
    r is the number of rows in the grid
    c is the number of cols in the grid
    Time: O(r*c)
    Space: O(1)
    ```

15. [**Closest Carrot**] Given a grid where `O`s are open spaces, `X`s are walls and `C`s are carrots and a starting row and column. Write a function to return the length of the shortest path from the starting point to the carrot.

    ```python
    def closestCarrot(grid, starting_row, starting_col):
      visited = set((starting_row, starting_col))
      q = [(starting_row, starting_col, 0)]
      while q:
        (r, c, dist) = q.pop(0)
        if grid[r][c] == 'C': return dist

        deltas = [(1,0), (-1,0), (0,1), (0,-1)]
        for delta_row, delta_col in deltas:
          neig_row = r + delta_row
          neig_col = c + delta_col
          row_inbounds = 0 <= neig_row < len(grid)
          col_inbounds = 0 <= neig_col < len(grid[0])

          pos = (neig_row, neig_col)
          if row_inbounds and col_inbounds and grid[neig_row, neig_col] != 'X' and pos not in visited:
            visited.add(pos)
            q.append((neig_row, neig_col, dist+1))
      return -1

    ```

    ```
    r is the number of rows in the grid
    c is the number of cols in the grid
    Time: O(r*c)
    Space: O(r*c)
    ```

16. [**Best Bridge**] Given a grid where `W` is water and `L` is land, with exactly two islands, write a function to return the minimum length bridge needed to connect both islands.

    ```python
    def bestBridge(grid):
      mainIsland = None
      for r in range(len(grid)):
        for c in range(len(grid[0])):
          potentialIsland = explore(grid, r, c, set())
          if len(potentialIsland) > 0:
            mainIsland = potentialIsland
            break

      visited = set(mainIsland)
      q = []
      for r,c in mainIsland:
        q.append((r,c,0))
      while q:
        r,c,dist = q.pop(0)
        if grid[r][c] == 'L' and (r,c) not in mainIsland:
          return dist - 1
        deltas = [(1,0), (-1,0), (0,1), (0,-1)]
        for delta_row, delta_col in deltas:
          neig_row, neig_col = r+delta_row, c+delta_col
          neig_pos = (neig_row, neig_col)
          if isInbounds(grid, neig_row, neig_col) and neig_pos not in visited:
            visited.add(neig_pos)
            q.append((neig_row, neig_col, dist+1))

    def isInbounds(grid, r, c):
      rowInbounds = 0 <= r < len(grid)
      colInbounds = 0 <= c < len(grid[0])
      return rowInbounds and colInbounds

    def explore(grid, r, c, visited):
      pos = (r,c)
      if not isInbounds(grid, r, c) or grid[r][c] == 'W' or pos in visited: return visited
      visited.add(pos)

      explore(grid, r-1, c, visited)
      explore(grid, r+1, c, visited)
      explore(grid, r, c-1, visited)
      explore(grid, r, c+1, visited)
      return visited
    ```

    ```
    r is the number of rows in the grid
    c is the number of cols in the grid
    Time: O(r*c)
    Space: O(r*c)
    ```

17. [**Longest Path**] Given a DAG as an adjacency list, write a function to return the length of the longest path within the graph.

    ```python
    def longestPath(graph):
      dist = {}
      for n in graph:
        if len(graph[n]) == 0: dist[n] = 0
      for n in graph:
        dist[n] = explore(graph, n, dist)
      return max(dist.values())

    def explore(graph, node, dist):
      if node in dist: return dist[node]
      max_length = 0
      for n in graph[node]:
        length = explore(graph, n, dist)
        max_length = max(max_length, length)
      return 1 + max_length
    ```

    ```python
    def longestPath(graph):
      dist = {}
      for n in graph:
        if len(graph[n]) == 0: dist[n] = 0
      for n in graph:
        explore(graph, n, dist)
      return max(dist.values())

    def explore(graph, node, dist):
      if node in dist: return dist[node]
      max_length = 0
      for n in graph[node]:
        length = explore(graph, n, dist)
        max_length = max(max_length, length)
      dist[node] = 1 + max_length
      return dist[node]
    ```

    ```
    n is the number of nodes in the graph
    Time: O(n)
    Space: O(n)
    ```

18. [**Semesters Required**] Given a number of courses `n`, and a list of prerequisites, write a function to return the minimum number of semesters required to take all `n` courses.

    ```python
    def semesterRequired(num_courses, prereqs):
      graph = buildGraph(num_courses, prereqs)
      dist = {}
      for n in graph:
        if len(graph[n]) == 0:
          dist[n] = 1
      for n in graph:
        dist[n] = explore(graph, n, dist)
      return max(dist.values())

    def buildGraph(num_courses, prereqs):
      graph = {n:[] for n in range(num_courses)}
      for a,b in prereqs:
        graph[a].append(b)
      return graph

    def explore(graph, node, dist):
      if node in dist: return dist[node]
      max_length = 0
      for n in graph[node]:
        length = explore(graph, n, dist)
        max_length = max(max_length, length)
      return 1 + max_length
    ```

    ```
    n is the number of nodes in the graph
    Time: O(n)
    Space: O(n)
    ```

19. [**Has Cycle**] Given a directed graph as an object/ asjacency list, write a function to return a boolean indicating whether or not the graph has cycles.

    ```python
    def hasCycle(graph):
      visiting = set()
      visited = set()

      for node in graph:
        if detectCycle(graph, node, visited, visiting): return True
      return False

    def detectCycle(graph, node, visited, visiting):
      if node in visited: return False
      if node in visiting: return True
      visiting.add(node)

      for n in graph[node]:
        if detectCycle(graph, n, visited, visiting): return True
      visiting.remove(node)
      visited.add(node)
      return False
    ```

    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n)
    ```

20. [**Prereqs Possible**] Given a number of courses `n` (0 - n-1) and an edge list of prereqs as arguments (as a directed graph), write a function to return a boolean indicating whether or not it is possible to complete all courses.

    ```python
    def prereqsPossibel(num_courses, prereqs):
      visiting = set()
      visited = set()
      graph = buildGraph(num_courses, prereqs)
      for node in graph:
        if detectCycle(graph, node, visited, visiting): return False
      return True

    def detectCycle(graph, node, visited, visiting):
      if node in visited: return False
      if node in visiting: return True
      visiting.add(node)

      for n in graph[node]:
        if detectCycle(graph, n, visited, visiting): return True
      visiting.remove(node)
      visited.add(node)
      return False

    def buildGraph(num_courses, prereqs):
      graph = {n:[] for n in range(num_courses)}
      for a,b in prereqs:
        graph[a].append(b)
      return graph
    ```

    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n)
    ```

21. [**Can Color**] Given a undirected graph as an adjacency list, write a function that returns a boolean indicating whether or not it's possible to color nodes of the graph using two colors such that no adjacent nodes have the same color.

    ```python
    def canColor(graph):
      coloring = {}
      for node in graph:
        if node not in coloring and validate(graph, node, coloring, True) == False:
          return False
      return True

    def validate(graph, node, coloring, current_color):
      if node in coloring: return current_color == coloring[node]
      coloring[node] = current_color
      for n in graph[node]:
        if validate(graph, n, coloring, not current_color) == False: return False
      return True
    ```
    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n)
    ```

22. [**Tolerant Teams**] Given a list of rivalries as an edge list (pairs of people that should NOT be on the same team), write a function that returns a boolean indicating whether or not it's possible to seperate people into two teams without rivals being on the same team.

    ```python
    def tolerant_teams(rivalries):
      graph = buildGraph(rivalries)
      coloring = {}
      for node in graph:
        if node not in coloring and validate_teams(graph, node, coloring, True) == False:
          return False
      return True

    def validate_teams(graph, node, coloring, current_color):
      if node in coloring: return current_color == coloring[node]
      coloring[node] = current_color
      for n in graph[node]:
        if validate_teams(graph, n, coloring, not current_color) == False: return False
      return True

    def buildGraph(edges):
      graph = {}
      for a, b in edges:
        if a not in graph: graph[a] = []
        if b not in graph: graph[b] = []
        graph[a].append(b)
        graph[b].append(a)
      return graph
    ```
    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n)
    ```

23. [**Unique Routing**] Given a list of cities `n` and a Undirected graph as a list of tuples (edge list) that represents a direct road that connects a pair of cities. Write a function that returns a boolean indicating whether or not there exists a unique route for every pair of cities.

    ```python
    def rare_routing(n, roads):
      graph = buildGraph(n, roads)
      visited = set()
      valid = validate_routes(graph, 0, visited, None)
      return valid and len(visited)==n

    def validate_routes(graph, node, visited, last_node):
      if node in visited: return False
      visited.add(node)
      
      for n in graph[node]:
        if n != last_node and validate_routes(graph, n, visited, node) == False: return False
      return True

    def buildGraph(n, edges):
      graph = {}
      for city in range(n): graph[city] = []
      for a, b in edges:
        graph[a].append(b)
        graph[b].append(a)
      return graph
    ```
    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n)
    ```

24. [**Knight Moves**] Given a knight and a pawn on a chess board, wite a function to return the minimum possible number of moves the knight can travel to get to the pawn's position.

    ```python
    def knight_attack(n, kr, kc, pr, pc):
      visited = set([(kr,kc)])
      q = [(kr,kc,0)]
      while q:
        r,c,step = q.pop(0)
        if (r,c) == (pr,pc): return step
        possible_moves = getValidMoves(n, r, c)
        for pos in possible_moves:
          pos_r, pos_c = pos
          if pos not in visited:
            q.append((pos_r, pos_c, step+1))
            visited.add(pos)
      return None

    def getValidMoves(n, r, c):
      positions = [
        (r+2, c+1),(r-2, c+1),(r+2, c-1),(r-2, c-1),
        (r+1, c+2),(r-1, c+2),(r+1, c-2),(r-1, c-2),
      ]
      inbound_positions = []
      for pos in positions:
        new_r, new_c = pos
        if 0 <= new_r < n and 0 <= new_c < n:
          inbound_positions.append(pos)
      return inbound_positions
    ```

    ```
    n is the number of nodes in the graph
    Time: O(n^2)
    Space: O(n^2)
    ```


---

### Dynamic Programming

1. [**Factorial Trailing Zeros**] [[**Leetcode 509**](https://leetcode.com/problems/factorial-trailing-zeroes/)] Given an integer `n`, return the number of trailing zeros in `n!`.

   ```python
   def trailingZeros(n):
    count = 0
    while n > 0:
      n //= 5
      count += n
    return count
   ```

   ```python
   def trailingZeros(n):
    if n == 0: return 0
    return n//5 + trailingZeros(n//5)
   ```

   ```python
   def trailingZeros(n):
    return 0 if n == 0 else n//5 + trailingZeros(n//5)
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

2. [**Fibonacci**] [[**Leetcode 509**](https://leetcode.com/problems/fibonacci-number/)] Given a number n, writhe a function to return the n-th number in the Fibonacci sequence.

   ```python
   def fib(n, memo={}):
    if n in memo: return memo[n]
    if n <= 2: return 1
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]
   ```

   ```python
   def fib(n):
    if n < 1: return 0
    dp = [0]*(n+1)
    dp[1] = 1
    for i in range (2, n+1):
      dp[i] = dp[i-1] + dp[i-2]
    return dp[-1]
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

   ```python
   def fib(n):
    if n < 2: return n
    one, two = 0, 1
    for i in range (2, n+1):
      one, two = two, one + two
    return two
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(1)
   ```

3. [**Climbing Stairs**] [[**Leetcode 70**](https://leetcode.com/problems/climbing-stairs/)]] Given a number n, write a function to return the n-th number in the Fibonacci sequence.

   ```python
   def climbingStairs(n, memo={}):
    if n in memo: return memo[n]
    if n <= 2: return n
    memo[n] = climbingStairs(n-1, memo) + climbingStairs(n-2, memo)
    return memo[n]
   ```

   ```python
   def climbingStairs(n):
    if n < 1: return 0
    dp = [0]*(n+1)
    dp[0], dp[1] = 1, 1
    for i in range (2, n+1):
      dp[i] = dp[i-1] + dp[i-2]
    return dp[-1]
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

   ```python
   def climbingStairs(n):
    one, two = 1, 1
    for i in range (2, n+1):
      one, two = two, one + two
    return two
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(1)
   ```

4. [**Tribonacci**] Given a number n, write a function to return the n-th number in the Tribonacci sequence.

   ```python
   def trib(n, memo={}):
    if n in memo: return memo[n]
    if n <= 1: return 0
    if n == 2: return 1
    memo[n] = trib(n-1, memo) + trib(n-2, memo) + trib(n-3, memo)
    return memo[n]
   ```

   ```python
   def trib(n):
    if n < 2: return 0
    dp = [0]*(n+1)
    dp[2] = 1
    for i in range (3, n+1):
      dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
    return dp[-1]
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(n)
   ```

   ```python
   def trib(n):
    if n < 2: return 0
    one, two, three = 0, 0, 1
    for i in range (3, n+1):
      one, two, three = two, three, (one + two + three)
    return three
   ```

   ```
     n is the length of the string
     Time: O(n)
     Space: O(1)
   ```

5. [**Non Adjcent Sum**] Given a list of numbers, write a function to return the maximum sum of non-adjacent items in the list. There is no limit to how many times items from the list can be used.

   ```python
   def nonAdjacentSum(nums, memo={}):
    key = ','.join(str(nums))
    if key in memo: return memo[key]
    if not nums: return 0
    include_first = nums[0] + nonAdjacentSum(nums[2:], memo)
    exclude_first = nonAdjacentSum(nums[1:], memo)
    memo[key] = max(include_first, exclude_first)
    return memo[key]
   ```
   ```python
   def nonAdjacentSum(nums):
    return _nonAdjacentSum(nums, 0)
    
   def _nonAdjacentSum(nums, i, memo={}):
    if i in memo: return memo[i]
    if i >= len(nums): return 0
    include_first = nums[i] + _nonAdjacentSum(nums, i+2, memo)
    exclude_first = _nonAdjacentSum(nums, i+1, memo)
    memo[i] = max(include_first, exclude_first)
    return memo[i]
   ```
   ```python
   def nonAdjacentSum(nums):
    if not nums: return 0
    if len(nums) < 3: return max(nums)
    dp = [0]*len(nums)
    dp[0], dp[1] = nums[0], max(nums[0], nums[1])
    for i in range(2, len(dp)):
      dp[i] = max(nums[i] + dp[i-2], dp[i-1])
    return dp[-1]
   ```
   ```python
   def nonAdjacentSum(nums):
    r1, r2 = 0, 0
    for num in nums:
      r1, r2 = r2, max(r1+num, r2)
    return r2  
   ```

   ```
     a is the amount given
     n is the length of the array
     Time: O(a*n)
     Space: O(a)
   ```

6. [**House Robber**] [[**Leetcode 198**](https://leetcode.com/problems/house-robber/)]] Given a list of numbers representing houses with money in them, write a function to return the maximum amount of money you can get by robbing non-adjacent houses.

   ```python
   def rob(nums, memo={}):
    key = ','.join(str(nums))
    if key in memo: return memo[key]
    if not nums: return 0
    include_first = nums[0] + rob(nums[2:], memo)
    exclude_first = rob(nums[1:], memo)
    memo[key] = max(include_first, exclude_first)
    return memo[key]
   ```
   ```python
   def rob(nums):
    def helper(nums, i, memo={}):
      if i in memo: return memo[i]
      if i >= len(nums): return 0
      include_first = nums[i] + helper(nums, i+2, memo)
      exclude_first = rob(nums, i+1, memo)
      memo[i] = max(include_first, exclude_first)
      return memo[i]
    return helper(nums, 0)
   ```
   ```python
   def rob(nums):
    if not nums: return 0
    if len(nums) < 3: return max(nums)
    dp = [0]*len(nums)
    dp[0], dp[1] = nums[0], max(nums[0], nums[1])
    for i in range(2, len(dp)):
      dp[i] = max(nums[i] + dp[i-2], dp[i-1])
    return dp[-1]
   ```
   ```python
   def rob(nums):
    r1, r2 = 0, 0
    for num in nums:
      r1, r2 = r2, max(r1+num, r2)
    return r2  
   ```

   ```
     a is the amount given
     n is the length of the array
     Time: O(a*n)
     Space: O(a)
   ```

7. [**House Robber II**] [[**Leetcode 213**](https://leetcode.com/problems/house-robber-ii/)]] Given a circular list of numbers representing houses with money in them, write a function to return the maximum amount of money you can get by robbing non-adjacent houses (cant rob both first and last houses as they are adjacent in a circular street).

   ```python
   def rob(nums):
    def helper(nums):
      r1, r2 = 0, 0
      for num in nums:
        r1, r2 = r2, max(r1+num, r2)
      return r2  
    return max(helper(nums[:-1]), helper(nums[1:]))
   ```

   ```
     a is the amount given
     n is the length of the array
     Time: O(a*n)
     Space: O(a)
   ```

8. [**House Robber III**] [[**Leetcode 337**](https://leetcode.com/problems/house-robber-iii/)]] Given a binary tree representing houses with money in them, write a function to return the maximum amount of money you can get by robbing non-adjacent houses (houses with direct link).

   ```python
   @lru_cache
   def rob(root, canRob=True):
    if not root: return 0
    include_root = root.val + rob(root.left, False) + rob(root.right, False) if canRob else 0
    exclude_root = rob(root.left, True) + rob(root.right, True)
    return max(include_root, exclude_root)
   ```
   ```python
   def rob(root):
    if root in memo: return memo[root]
    if not root: return 0
    include_root, exclude_root = root.val, rob(root.left) + rob(root.right)
    if root.left: include_root += rob(root.left.left) + rob(root.left.right)
    if root.right: include_root += rob(root.right.left) + rob(root.right.right)
    memo[root] = max(include_root, exclude_root)
    return memo[root]
   ```
   ```
     a is the amount given
     n is the length of the array
     Time: O(a*n)
     Space: O(a)
   ```


9. [**Unique Paths**] [[**Leetcode 62**](https://leetcode.com/problems/unique-paths/)]] Given a `m x n` grid and a robot positioned at the top-left corner, write a function to return the number of possible unique paths to get to the bottom-right corner.

   ```python
   def gridTravler(m, n, memo={}):
    key = (m,n)
    if key in memo: return memo[key]
    if m==0 or n==0: return 0
    if m==1 or n==1: return 1
    memo[key] = gridTravler(m, n-1, memo) + gridTravler(m-1, n, memo)
    return memo[key]
   ```
   ```python
   def gridTravler(m, n, memo={}):
    grid = [[0 for j in range(n+1)] for i in range(m+1)]
    grid[1][1] = 1
    for r in range(1, m+1):
      for c in range(1, n+1):
        if r==1 and c==1: continue
        grid[r][c] = grid[r-1][c] + grid[r][c-1]
    return grid[-1][-1]
   ```
   ```
     m is the number of rows in the grid
     n is the number of columns in the grid
     Time: O(m*n)
     Space: O(n)
   ```

10. [**Unique Paths II**] [[**Leetcode 63**](https://leetcode.com/problems/unique-paths-ii/)]] Given a `m x n` integer grid where `1` represents obstacles and `0`represents open spaces; and a robot positioned at the top-left corner, write a function to return the number of possible unique paths to get to the bottom-right corner.

    ```python
    def uniquePaths(grid):
      return countPaths(grid, r, c)
    def countPaths(grid, r, c, memo={}):
      key = (r,c)
      if key in memo: return memo[key]
      if r >= len(grid) or c >= len(grid[0]) or grid[r][c]=="1": return 0
      if r == len(grid)-1 or c == len(grid[0])-1: return 1
      memo[key] = countPaths(grid, r+1, c, memo) + countPaths(grid, r, c+1, memo)
      return memo[key]
    ```
    ```
      m is the number of rows in the grid
      n is the number of columns in the grid
      Time: O(m*n)
      Space: O(n*n)
    ```

11. [**Min Path Sum**] [[**Leetcode 64**](https://leetcode.com/problems/minimum-path-sum/)]] Given a `m x n` integer grid, write a function the return the minimum sum possible by traveling from the top-left corner to the bottom-right corner. You can only travel by moving down or right.

    ```python
    def minPathSum(grid):
      def dfs(grid, r, c, memo={}):
        key = (r,c)
        if key in memo: return memo[key]
        if r >= len(grid) or c >= len(grid[0]): return float('inf')
        if r == len(grid)-1 and c == len(grid[0])-1: return grid[r][c]
        min_path = min(dfs(grid, r+1, c, memo), dfs(grid, r, c+1, memo))
        memo[key] = grid[r][c] + min_path
        return memo[key]
      return dfs(grid, 0, 0)
    ```

    ```
      m is the number of rows in the grid
      n is the number of columns in the grid
      Time: O(m*n)
      Space: O(n*n)
    ```

12. [**Max Path Sum**] Given a `m x n` integer grid, write a function the return the maximum sum possible by traveling from the top-left corner to the bottom-right corner. You can only travel by moving down or right.

    ```python
    def maxPathSum(grid):
      def dfs(grid, r, c, memo={}):
        key = (r,c)
        if key in memo: return memo[key]
        if r >= len(grid) or c >= len(grid[0]): return float('-inf')
        if r == len(grid)-1 and c == len(grid[0])-1: return grid[r][c]
        max_path = max(dfs(grid, r+1, c, memo), dfs(grid, r, c+1, memo))
        memo[key] = grid[r][c] + max_path
        return memo[key]
      return dfs(grid, 0, 0)
    ```

    ```
      m is the number of rows in the grid
      n is the number of columns in the grid
      Time: O(m*n)
      Space: O(n*n)
    ```

13. [**Can Sum**] Given a target amount and a list of positive numbers. Write a function to return a boolean indicating whether or not it's possible to create the amount. You can reuse numbers of the list as needed.

    ```python
    def canSum(target, nums, memo={}):
      if target in memo: return memo[target]
      if target == 0: return True
      if target < 0: return False
      for n in nums:
        rem = target - n
        if canSum(rem, nums, memo):
          memo[target] = True
          return memo[target]
      memo[target] = False
      return memo[target]
    ```

    ```python
    def canSum(target, nums):
      dp = [False]*(target+1)
      dp[0] = True
      for i in range(1, target+1):
        for n in nums:
          if i-n >=0: dp[i] = dp[i-n]
      return dp[-1]
    ```

    ```python
    def canSum(target, nums):
      q = [target]
      visited = set([target])
      while q:
        cur_amt = q.pop(0)
        if cur_amt == 0: return True
        for n in nums:
          new_cur_amt = cur_amt - n
          if new_cur_amt not in visited and new_cur_amt >= 0:
            q.append(new_cur_amt)
            visited.add(new_cur_amt)
      return False
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a*n)
      Space: O(a)
    ```


14. [**Count Sum**] Given a target amount and a list of positive numbers. Write a function to return an integer representing the total number of ways to create the target amount by adding numbers in the list. You can reuse numbers of the list as needed.

    ```python
    def countSum(target, nums, memo={}):
      if target in memo: return memo[target]
      if target == 0: return 1
      if target < 0: return 0
      count = 0
      for n in nums:
        rem = target - n
        count += countSum(rem, nums, memo)
      memo[target] = count
      return memo[target]
    ```

    ```python
    def countSum(target, nums):
      dp = [0]*(target+1)
      dp[0] = 1
      for i in range(1, target+1):
        for n in nums:
          if i-n >=0: dp[i] += dp[i-n]
      return dp[-1]
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a*n)
      Space: O(a)
    ```

15. [**How Sum**] Given a target amount and a list of positive numbers. Write a function to return an array (of any combination) that adds up to exactly the target amount. If no such array exists, then return None.

    ```python
    def howSum(target, nums, memo={}):
      if target in memo: return memo[target]
      if target == 0: return []
      if target < 0: return None
      for n in nums:
        rem = target - n
        rem_combo = howSum(rem, nums, memo)
        if rem_combo != None:
          memo[target] = [*rem_combo, n]
          return memo[target]
      memo[target] = None
      return memo[target]
    ```

    ```python
    def howSum(target, nums):
      dp = [None]*(target+1)
      dp[0] = []
      for i in range(1, target+1):
        for n in nums:
          if i-n >= 0 and dp[i-n] != None: dp[i] = [*dp[i-n], n]
      return dp[-1]
    ```

    ```python
    def howSum(target, nums):
      q = [(target, [])]
      visited = set([target])
      while q:
        cur_amt, cur_combo = q.pop(0)
        if cur_amt == 0: return cur_combo
        for n in nums:
          new_cur_amt = cur_amt - n
          if new_cur_amt not in visited and new_cur_amt >= 0:
            q.append((new_cur_amt, [*cur_combo, n]))
            visited.add(new_cur_amt)
      return None
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a*n)
      Space: O(a)
    ```


16. [**Best Sum**] Given a target amount and a list of positive numbers. Write a function to return the shortest array (of any combination) that adds up to exactly the target amount. If no such array exists, then return None.

    ```python
    def bestSum(target, nums, memo={}):
      if target in memo: return memo[target]
      if target == 0: return []
      if target < 0: return None
      shortest_combo = None
      for n in nums:
        rem = target - n
        rem_combo = bestSum(rem, nums, memo)
        if rem_combo != None:
          target_combo = [*rem_combo, n]
          if shortest_combo == None or len(target_combo) < len(shortest_combo):
            shortest_combo = target_combo
      memo[target] = shortest_combo
      return memo[target]
    ```

    ```python
    def bestSum(target, nums):
      dp = [None]*(target+1)
      dp[0] = []
      for i in range(1, target+1):
        shortest_combo = None
        for n in nums:
          if i-n >= 0 and dp[i-n] != None:
            target_combo = [*dp[i-n], n]
            if shortest_combo == None or len(target_combo) < len(shortest_combo):
              shortest_combo = target_combo
          dp[i] = shortest_combo
      return dp[-1]
    ```

    ```python
    def bestSum(target, nums):
      q = [(target, [])]
      visited = set([target])
      while q:
        cur_amt, cur_combo = q.pop(0)
        if cur_amt == 0: return cur_combo
        for n in nums:
          new_cur_amt = cur_amt - n
          if new_cur_amt not in visited and new_cur_amt >= 0:
            q.append((new_cur_amt, [*cur_combo, n]))
            visited.add(new_cur_amt)
      return None
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a^2 *n)
      Space: O(a)
    ```

17. [**Combination Sum**] [[**Leetcode 39**](https://leetcode.com/problems/combination-sum/)] Given a target amount and a list of distinct numbers. Write a function to return all the possible unique combinations to make change for the given amount.

    ```python
    def combinationSum(amount, nums):
      if amount == 0: return [[]]
      if amount < 0: return None
      all_combo = []
      for n in nums:
        rem = amount-n
        rem_combo = combinationSum(rem, nums)
        if rem_combo != None:
          target_combo = [[n, *way] for way in rem_ways]
          for item in target_combo:
            item.sort()
            if item not in all_combo: all_combo.append(item)
      return all_combo
    ```

    ```
      a is the amount given
      c is the number of coins
      Time: O(a*c)
      Space: O(ac)
    ```

18. [**Target Sum**] [[**Leetcode 494**](https://leetcode.com/problems/target-sum/)] Given a target amount and a list of numbers. Write a function to return the number of different expressions that can be built to add up to the target by adding a `-` or `+` in front of each item in the list.

    ```python
    def targetSumWays(target, nums):
      def dfs(idx, total, memo={}):
        if (idx, total) in memo: return memo[(idx, total)]
        if idx == len(nums): return 1 if (total==target) else 0
        memo[(idx, total)] = dfs(idx+1, total+nums[idx]) + dfs(idx+1, total-nums[idx])
        return memo[(idx, total)]
      return dfs(0,0)
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a*n)
      Space: O(a)
    ```

19. [**Coin Change**] [[**Leetcode 322**](https://leetcode.com/problems/coin-change/)] Given a target amount and a list of numbers representing coins. Write a function to return the fewest number of coins to create the amount. You can reuse as many coins as needed.

    ```python
    def coinChange(amount, coins):
      def dfs(amount, coins, memo={}):
        if amount in memo: return memo[amount]
        if amount < 0: return float('inf')
        if amount == 0: return 0
        min_coins = float('inf')
        for c in coins:
          num_coins = 1 + dfs(amount-c, coins)
          min_coins = min(min_coins, num_coins)
        memo[amount] = min_coins
        return min_coins
      result = dfs(amount, coins)
      return result if result != float('inf') else -1
    ```

    ```python
    def coinChange(amount, coins):
      dp = [float('inf')]*(amount+1)
      dp[0] = 0
      for a in range(1, amount+1):
        for c in coins:
          if a - c >= 0: dp[a] = min(dp[a], 1+dp[a-c])
      return dp[-1] if dp[-1] != float('inf') else -1
    ```

    ```python
    def coinChange(amount, coins):
      q = deque([(amount, 0)])
      visited = set()
      while q:
        cur_amt, num_coins = q.popleft()
        if cur_amt == 0: return num_coins
        for c in coins:
          new_cur_amt = cur_amt - c
          if new_cur_amt not in visited and new_cur_amt >= 0:
            q.append((new_cur_amt, 1+num_coins))
            visited.add(new_cur_amt)
      return -1
    ```

    ```
      a is the amount given
      n is the length of the array
      Time: O(a*n)
      Space: O(a)
    ```

20. [**Coin Change II**] [[**Leetcode 518**](https://leetcode.com/problems/coin-change-ii/)] Given a target amount and a list of numbers representing coins. Write a function to return the number of different ways to make change for the given amount.

    ```python
    def coinChangeII(amount, coins):
      def dfs(amount, coins, i, memo={}):
        key = (amount,i)
        if key in memo: return memo[key]
        if amount == 0: return 1
        if i >= len(coins): return 0
        total, coin = 0, coins[i]
        for qty in range(0, (amount//coin)+1):
            rem = amount - (qty*coin)
            total += dfs(rem, coins, i+1, memo)
        memo[key] = total
        return total
      return dfs(amount, coins, 0)
    ```

    ```python
    def coinChangeII(amount, coins):
      dp = [0]*(amount+1)
      dp[0] = 1
      for c in coins:
        for a in range(1, amount+1):
          if a - c >= 0:
            dp[a] += dp[a-c]
      return dp[-1]
    ```

    ```
      a is the amount given
      c is the number of coins
      Time: O(a*c)
      Space: O(ac)
    ```

21. [**Coin Change III**] Given a target amount and a list of distinct numbers representing coins. Write a function to return all the possible unique to make change for the given amount.

    ```python
    def coinChangeWays(amount, coins):
      if amount == 0: return [[]]
      if amount < 0: return None
      res = []
      for c in coins:
        rem = amount-c
        rem_ways = coinChangeWays(rem, coins)
        if rem_ways != None:
          all_ways = [[c, *way] for way in rem_ways]
          for item in all_ways:
            item.sort()
            if item not in res: res.append(item)
      return res
    ```

    ```
      a is the amount given
      c is the number of coins
      Time: O(a*c)
      Space: O(ac)
    ```

22. [**Word Break**] [[**Leetcode 139**](https://leetcode.com/problems/word-break/)] Given a target string and a list of words. Write a function to return a boolean indicating whether or not it's possible to create the target string by concatenating words of the list together. You can reuse words as needed.

    ```python
    def canConstruct(target, word_bank, memo={}):
      if target in memo: return memo[target]
      if target == "": return True
      for w in word_bank:
        if target.startswith(w):
          surfix = target[len(w):]
          if canConstruct(surfix, word_bank, memo):
            memo[target] = True
            return memo[target]
      memo[target] = False
      return memo[target]
    ```

    ```python
    def canConstruct(target, word_bank):
      dp = [False]*(len(target)+1)
      dp[0] = True
      for i in range(0, len(target)+1):
        for w in word_bank:
          if target[i:i+len(w)] == w:
            dp[i + len(w)] = True
      return dp[-1]
    ```

    ```
      a is the length of the target string
      n is the length of the word array
      Time: O(a^2 * n)
      Space: O(a)
    ```

23. [**Count Construct**] Given a target string and a list of words. Write a function to return an integer representing the total number of ways to create the target string by concatenating words of the list together. You can reuse words as needed.

    ```python
    def countConstruct(target, word_bank, memo={}):
      if target in memo: return memo[target]
      if target == "": return 1
      count = 0
      for w in word_bank:
        if target.startswith(w):
          surfix = target[len(w):]
          count += countConstruct(surfix, word_bank, memo)
      memo[target] = count
      return memo[target]
    ```

    ```python
    def canConstruct(target, word_bank):
      dp = [0]*(len(target)+1)
      dp[0] = 1
      for i in range(0, len(target)+1):
        for w in word_bank:
          if target[i: i+len(w)] == w: 
            dp[i + len(w)] += dp[i]
      return dp[-1]
    ```

    ```
      a is the length of the target string
      n is the length of the word array
      Time: O(a^2 * n)
      Space: O(a)
    ```

24. [**Best Construct**] Given a target string and a list of words. Write a function to return an integer representing the minimum number of words needed to create the target string by concatenating words of the list together. You can reuse words as needed.

    ```python
    def bestConstruct(target, word_bank, memo={}):
      if target in memo: return memo[target]
      if target == "": return 0
      min_words = float('inf')
      for w in word_bank:
        if target.startswith(w):
          surfix = target[len(w):]
          num_words = 1 + bestConstruct(surfix, word_bank, memo)
          min_words = min(min_words, num_words)
      memo[target] = min_words
      return memo[target]
    ```

    ```python
    def bestConstruct(target, word_bank):
      dp = [float('inf')]*(len(target)+1)
      dp[0] = 0
      for i in range(0, len(target)+1):
        for w in word_bank:
          if target[i: i+len(w)] == w: 
            dp[i + len(w)] = min(dp[i + len(w)], 1+dp[i])
      return dp[-1]
    ```

    ```
      a is the length of the target string
      n is the length of the word array
      Time: O(an)
      Space: O(a)
    ```

25. [**All Construct**] Given a target string and a list of words. Write a function to return a 2D array containing all the ways to create the target string by concatenating words of the list together. You can reuse words as needed.

    ```python
    def allConstruct(target, word_bank, memo={}):
      if target in memo: return memo[target]
      if target == "": return [[]]
      all_ways = []
      for w in word_bank:
        if target.startswith(w):
          surfix = target[len(w):]
          surfix_ways = allConstruct(surfix, word_bank, memo)
          target_ways = [[word, *way] for way in surfix_ways]
          for item in target_ways: 
            all_ways.append(item)
      memo[target] = all_ways
      return memo[target]
    ```

    ```
      a is the length of the target string
      n is the length of the word array
      Time: O(a^2 * n)
      Space: O(a)
    ```


26. [**Word Break II**] [[**Leetcode 140**](https://leetcode.com/problems/word-break-ii/)] Given a target string `s` and a list of words `wordDict`. Write a function to add spaces in `s` to construct a sentence where each word is a vaild word in the `wordDict`. You can reuse words as needed.

    ```python
    def wordBreak(s, wordDict):
      if s == '': return ['']
      all_ways = []
      for w in wordDict:
        if s.startswith(w):
          surfix = s[len(w):]
          surfix_ways = wordBreak(surfix, wordDict)
          target_ways = [f'{w} {way}' for way in surfix_ways]
          for item in target_ways:
            all_ways.append(item)
      return all_ways
    ```

    ```
      a is the length of the target string
      n is the length of the word array
      Time: O(a^2 * n)
      Space: O(a)
    ```

27. [**Summing Squares**] Given a  number `n`, write a function to return the minimum number of perfect squares that sum to the target.

    ```python
    def summingSquares(n, memo={}):
      if n in memo: return memo[n]
      if n == 0: return 0
      min_count = float("inf")
      for i in range(1, int(n**(1/2))+1):
        rem = n - i*i
        count = 1 + summingSquares(rem, memo)
        min_count = min(min_count, count)
      memo[n] = min_count
      return memo[n]
    ```

    ```
      n is the number given
      Time: O(n * sqrt(n))
      Space: O(n)
    ```

28. [**Placng Plants**] Given a 2D list of dimensions `n` * `m` where each row represents a list of costs of flower types at the specific position. Write a function that returns the minimum cost need to plant a flower at each position (can't plan same type of flower in adjacent positions).

    ```python
    def placePlants(costs, pos=0, last_type=None, memo={}):
      key = (pos, last_type)
      if key in memo: return memo[key]
      if pos >= len(costs): return 0

      min_cost = float('inf')
      for plant_type, plant_cost in enumerate(costs[pos]):
        if plant_type != last_type:
          candidate = plant_cost + placePlants(costs, pos+1, plant_type, memo)
          min_cost = min(min_cost, candidate)
      memo[key] = min_cost
      return memo[key]
    ```

    ```
      n is the number of garden positions
      m is the number of plant types
      Time: O(n*m)
      Space: O(n*m)
    ```

29. [**Jump Game**] [[**Leetcode 55**](https://leetcode.com/problems/jump-game/)] Given a list of numbers where each number represents the max number of steps to take, write a function to return a boolean indicating whether or not it is possible to get to the end of the list from the begining.

    ```python
    def canJump(nums, i=0, memo={}):
      if i in memo: return memo[i]
      if i >= len(nums)-1: return True
      for step in range(1, nums[i]+1):
        if canJump(nums, i+step, memo):
          memo[i] = True
          return memo[i]
      memo[i] = False
      return memo[i]
    ```

    ```python
    def canJump(nums):
      m = 0
      for i, step in enumerate(nums):
        if i > m: return False
        m = max(m, i+step)
      return True
    ```

    ```
      n is the number given
      Time: O(n^2)
      Space: O(n)
    ```

30. [**Longest Increasing Subsequence**] [[**Leetcode 300**](https://leetcode.com/problems/longest-increasing-subsequence/)]  Given an integer array, return the length of the longest strictly increasing subsequence.

    ```python
    def lengthOfLIS(numbers, previous=float('-inf'), memo={}):
      if not numbers: return 0
      key = (tuple(numbers),previous)
      if key in memo: return memo[key]

      current = numbers[0]
      options = []

      dont_take_current = lengthOfLIS(numbers[1:], previous, memo)
      options.append(dont_take_current)

      if current > previous:
        take_current = 1 + lengthOfLIS(numbers[1:], current, memo)
        options.append(take_current)
      
      memo[key] = max(options)
      return memo[key]
    ```
    ```python
    def lengthOfLIS(numbers, i=0, previous=float('-inf'), memo={}):
      if not numbers or i == len(numbers): return 0
      key = (i,previous)
      if key in memo: return memo[key]

      current = numbers[i]
      options = []

      dont_take_current = lengthOfLIS(numbers, i+1, previous, memo)
      options.append(dont_take_current)

      if current > previous:
        take_current = 1 + lengthOfLIS(numbers, i+1, current, memo)
        options.append(take_current)
      
      memo[key] = max(options)
      return memo[key]
    ```
    ```python
    def lengthOfLIS(numbers):
      LSI = [1]*len(numbers)
      for i in reversed(range(len(numbers))):
          for j in range(i + 1, len(numbers)):
              if numbers[i] < numbers[j]:
                  LSI[i] = max(LSI[i], 1+ LSI[j])
      return max(LSI)
    ```
    ```
    n is the number of nodes
    Time: O(n)
    Space: O(n)
    ```


31. [**Max Palindromic Subsequence**] Given a  string `n`, write a function to return the length of the longest subsequence of the string that is also a palindrome.

    ```python
    def maxPalinSubsequence(s, memo={}):
      if s in memo: return memo[s]
      if not s: return 0
      if len(s)==1: return 1

      if s[0] == s[-1]: memo[s] = 2 + maxPalinSubsequence(s[1:-1], memo)
      else: memo[s] = max(maxPalinSubsequence(s[0:-1], memo), maxPalinSubsequence(s[1:], memo))
      return memo[s]
    ```

    ```python
    def maxPalinSubsequence(s):
      def _maxPalinSubsequence(string, l=0, r=len(s)-1, memo={}):
        key = (l,r)
        if key in memo: return memo[key]
        if l > r: return 0
        if l == r: return 1

        if string[l] == string[r]: memo[key] = 2 + _maxPalinSubsequence(string, l+1, r-1, memo)
        else: memo[key] = max(_maxPalinSubsequence(string, l+1, r, memo), _maxPalinSubsequence(string, l, r-1, memo))
        return memo[key]
      return _maxPalinSubsequence(s)
    ```

    ```
      n is the nlength of the given string
      Time: O(n^2)
      Space: O(n^2)
    ```

32. [**Max Overlapping Subsequence**] Given two strings `s1` and `s2`, write a function to return the length of the longest overlapping subsequence of the string.

    ```python
    def overlap_subsequence(s1, s2, memo={}):
      key = s1+s2
      if key in memo: return memo[key]
      if len(s1) == 0 or len(s2) == 0: return 0
      if s1[0] == s2[0]: memo[key] = 1 + overlap_subsequence(s1[1:], s2[1:])
      else: memo[key] = max(overlap_subsequence(s1, s2[1:]), overlap_subsequence(s1[1:], s2))
      return memo[key]
    ```

    ```python
    def overlap_subsequence(s1, s2, i=0, j=0, memo={}):
      key = (i,j)
      if key in memo: return memo[key]
      if i == len(s1) or j == len(s2): return 0
      if s1[i] == s2[j]: memo[key] = 1 + overlap_subsequence(s1, s2, i+1, j+1)
      else: memo[key] = max(overlap_subsequence(s1, s2, i+1, j), overlap_subsequence(s1, s2, i, j+1))
      return memo[key]
    ```

    ```
      n is the nlength of the given string
      Time: O(n^2)
      Space: O(n^2)
    ```

33. [**Subsets of List**] Given a list as argument, write a function that returns a 2D list containing all possible subsets of the list argument. Assume input list contains unique elements and ignore order for the returned list.

    ```python
    def subsetOfLists(nums):
      if not nums: return [[]]
      exclude_first = subsetOfLists(nums[1:])
      include_first = []
      for item in exclude_first:
        include_first.append([nums[0], *item])
      return [*include_first, *exclude_first]
    ```
    ```
      n is the length of the list
      Time: O(n^2)
      Space: O(n^2)
    ```

34. [**Combinations of List**] Given a list and a length as arguments, write a function that returns a 2D list containing all possible combinations of the specified length within the list. Assume input list contains unique elements and ignore order for the returned list.

    ```python
    def combinationOfLists(nums, k):
      if len(nums) < k: return []
      if k == 0 or not nums: return [[]]
      exclude_first = combinationOfLists(nums[1:], k)
      include_first = []
      for combo in combinationOfLists(nums[1:], k-1):
        include_first.append([nums[0], *combo])
      return [*include_first, *exclude_first]
    ```
    ```
      n is the length of the list
      Time: O(n choose k)
      Space: O(n choose k)
    ```

35. [**Permutation of List**] Given a list as argument, write a function that returns a 2D list containing all possible permutations of the list argument. Assume input list contains unique elements and ignore order for the returned list.

    ```python
    def permutationOfLists(nums):
      if not nums: return [[]]
      exclude_first = permutationOfLists(nums[1:])
      include_first = []
      for perm in exclude_first:
        for i in range(len(perm)+1):
          include_first.append([*perm[:i], nums[0], *perm[i:]])
      return include_first
    ```
    ```
      n is the length of the list
      Time: O(n^2)
      Space: O(n^2)
    ```

36. [**Enclosed Possibilities**] Given a string containing parentheses as argument (for example `a(bc)de`), write a function to return a list containing all possible strings that could be generated by expanding all parenthesis. The string `a(bc)de` returns `['abde', 'acde']`.

    ```python
    def enclosedPossibilities(s):
      if not s: return ['']
      chars, rem = getOptions(s)
      suffixes = parenthetical_possibilities(rem)

      all_possibilities = []
      for c in chars:
        for suffix in suffixes:
          all_possibilities.append(''.join([c, *suffix]))
      return all_possibilities

    def getOptions(s):
      if s[0] == '(':
        end = s.index(')')
        chars, rem = s[1:end], s[end+1:]
      else:
        chars, rem = s[0], s[1:]
      return (chars, rem)
    ```
    ```python
    def enclosedPossibilities(s):
      if not s: return ['']
      chars, rem = getOptions(s)
      suffixes = parenthetical_possibilities(rem)

      all_possibilities = []
      for c in chars:
        for suffix in suffixes:
          all_possibilities.append(c + suffix)
      return all_possibilities

    def getOptions(s):
      if s[0] == '(':
        end = s.index(')')
        chars, rem = s[1:end], s[end+1:]
      else:
        chars, rem = s[0], s[1:]
      return (chars, rem)
    ```

    ```python
    def enclosedPossibilities(s):
      if not s: return ['']
      chars, rem = getOptions(s)
      suffixes = parenthetical_possibilities(rem)

      all_possibilities = []
      for c in chars:
        all_possibilities += [ char + suffix for suffix in suffixes ]
      return all_possibilities

    def getOptions(s):
      if s[0] == '(':
        end = s.index(')')
        chars, rem = s[1:end], s[end+1:]
      else:
        chars, rem = s[0], s[1:]
      return (chars, rem)
    ```
    ```
      n is the length of the string
      m is the length of the largest enclosed group
      Time: O(m^n)
      Space: O(m^n)
    ```


37. [**Substitute Synonyms**] Given a sentence as a string and a dictionary whose keys are words, and values are a list of synonyms to the corresponding key. Write a function that returns an array of all possible sentenses that can be formed by subsituting words from the input string with their synonyms. 

    ```python
    def subsituteSynonyms(sentence, synonyms):
      words = sentence.split(' ')
      subarrays = generate(words, synonyms)

      final_result = []
      for subarray in subarrays:
        final_result.append(' '.join(subarray))
      return final_result

    def generate(words, synonyms):
      if not words: return [[]]
      first_word, rem_words = words[0], words[1:]
      subarrays = generate(rem_words, synonyms)

      result = []
      if first_word in synonyms:
        for synonym in synonyms[first_word]:
          for subarray in subarrays:
            result.append([synonym, *subarray])
      else:
        for subarray in subarrays:
          result.append([first_word, *subarray])
      return result
    ```
    ```python
    def subsituteSynonyms(sentence, synonyms):
      words = sentence.split(' ')
      subarrays = generate(words, synonyms)
      return [' '.join(subarray) for subarray in subarrays]

    def generate(words, synonyms):
      if not words: return [[]]
      first_word, rem_words = words[0], words[1:]
      subarrays = generate(rem_words, synonyms)

      result = []
      if first_word in synonyms:
        for synonym in synonyms[first_word]:
          result += [ [synonym, *subarray] for subarray in subarrays ]
      else:
        result += [ [first_word, *subarray] for subarray in subarrays ]
      return result
    ```
    ```
      n is the number of words in the sentence
      m is the max number of synonyms for a word
      Time: O(m^n)
      Space: O(m^n)
    ```

38. [**Edit Distance**] [[**Leetcode 72**](https://leetcode.com/problems/edit-distance/)] Given two strings, write a function to compute the edit distance between both strings. Meaning how many changes to be made on one string to make it identical to the other string. Example, the edit distance of the two strings `pale` and `bale` is `1` because replacing the `p` with a `b` makes them equal. aka Levenshtein Distance.

    ```python
    def computeEditDistance(s, t):
      memo = {}
      def recurse(i, j):
        if (i,j) in memo: return memo[(i,j)]
        if i == 0: result = j
        elif j == 0: result = i
        elif s[i-1] == t[j-1]: result = recurse(i-1, j-1)
        else:
          subCost = 1 + recurse(i-1, j-1)
          delCost = 1 + recurse(i-1, j)
          insCost = 1 + recurse(i, j-1)
          result = min(subCost, delCost, insCost)
        memo[(i,j)] = result
        return result
      return recurse(len(s), len(t))
    ```
    ```python
    def computeEditDistance2(s, t):
      dp = [[0 for j in range(len(t)+1)] for i in range(len(s)+1)]
      for i in range(len(s)+1):
        for j in range(len(t)+1):
          if i == 0: dp[i][j] = j
          elif j == 0: dp[i][j] = i
          elif s[i-1] == t[j-1]: dp[i][j] = dp[i-1][j-1]
          else:
            subCost = 1 + dp[i-1][j-1]
            delCost = 1 + dp[i-1][j]
            insCost = 1 + dp[i][j-1]
            dp[i][j] = min(subCost, delCost, insCost)
      return dp[-1][-1]
    ```
    ```
      n is the length of s
      m is the lenth of t
      Time: O(m*n)
      Space: O(m*n)
    ```

39. [**One Away**] [[**Leetcode 161**](https://leetcode.com/problems/one-edit-distance/)] Given two strings, write a function to return a boolean indicating whether or not both strings can be made equal by using only one edit. Example, the edit distance of the two strings `pale` and `bale` is `1` because replacing the `p` with a `b` makes them equal.

    ```python
    def oneAway(s, t):
      dp = [[0 for j in range(len(t)+1)] for i in range(len(s)+1)]
      for i in range(len(s)+1):
        for j in range(len(t)+1):
          if i == 0: dp[i][j] = j
          elif j == 0: dp[i][j] = i
          elif s[i-1] == t[j-1]: dp[i][j] = dp[i-1][j-1]
          else: dp[i][j] = 1 + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1])
      return dp[-1][-1] <= 1
    ```
    ```python
    def oneAway(s, t):
      for i in range(min(len(s), len(t))):
        if s[i] != t[i]:
          if s[i+1:]==t[i+1:] or s[i:]==t[i+1:] or s[i+1:]==t[i:]: return True
          else: return False
      return True
    ```
    ```
      n is the length of s
      m is the lenth of t
      Time: O(min(m,n))
      Space: O(1)
    ```

40. [**Knight Moves**] Given a knight and a pawn on a chess board, wite a function to return the total number of ways the knight can travel to get to the pawn's position in exactly `m` moves/steps.

   ```python
   def knight_moves(n, m, kr, kc, pr, pc, memo={}):
    key = (m, kr, kc)
    if key in memo: return memo[key]
    if kr < 0 or kr >= n or kc < 0 or kc >= n: return 0
    if m == 0: return (kr, kc) == (pr, pc)
    possible_positions = [(kr+2, kc+1),(kr-2, kc+1),(kr+2, kc-1),(kr-2, kc-1),
                          (kr+1, kc+2),(kr-1, kc+2),(kr+1, kc-2),(kr-1, kc-2)]
    count = 0
    for new_r, new_c in possible_positions:
      count += knight_moves(n, m-1, new_r, new_c, pr, pc, memo)
    memo[key] = count
    return memo[key]
   ```

41. [**Restore IP Addresses**] given a string `s` containing only digits, write a function to return all possible valid IP addresses. A valid IP address consists of exactly four integers separated by single dots. Each integer is between 0 and 255 (inclusive) and cannot have leading zeros.

   ```python
   def restoreIpAddresses(s):
    def backtrack(s, ct, path, result):
      if ct == 4:
        if not s: result.append(path[:-1])
        return
      for i in range(1,4):
        if i > len(s): continue
        if i > 1 and s[0] == '0': continue
        if i > 2 and int(s[:3]) > 255: continue
        backtrack(s[i:], ct+1, path+s[:i]+'.', result)
    result = []
    backtrack(s, 0, "", result)
    return result
   ```
---

### Tries

1. [**Build Trie**] Given a string, implement a Trie data structure capable of storing the string/ word and also searching the trie if a word exists. For example, the words `hello`, `help`, and `hey` can be stored in the trie as below.

   ```python
     '''
      {h: {
        e: {
          l: {
            l: {o: {'*': True}}
            p: {'*': True}
          }
          y: {'*': True}
        }
      }}
     '''
   ```

   ```python
    class Trie:
      head = {}
      def add(self, word):
        cur = self.head
        for ch in word:
          if ch not in cur: cur[ch] = {}
          cur = cur[ch]
        cur['*'] = True
      
      def search(self, word):
        cur = self.head
        for ch in word:
          if ch not in cur: return False
          cur = cur[ch]
        if '*' in cur: return True
        else: return False
   ```

   ```
     n is the length of the word.
     Time: O(n)
     Space: O(n)
   ```

2. [**Search Trie**] Given the head of a trie and a string, write a function to return a boolean indicating whether or not the string is present in the trie.
   ```python    
    def search(self, head, word):
      cur = head
      for ch in word:
        if ch not in cur: return False
        cur = cur[ch]
      if '*' in cur: return True
      else: return False
   ```

   ```
     n is the length of the word.
     Time: O(n)
     Space: O(1)
   ```

3. [**Implement Trie (Prefix Tree)**] [[**Leetcode 208**](https://leetcode.com/problems/implement-trie-prefix-tree/)] A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. Implement one with features of `insert`, `search`, and `startsWith`.
   ```python  
    class Trie:
      def __init__(self):
        self.head = {}

      def insert(self, word: str) -> None:
        cur = self.head
        for ch in word:
          if ch not in cur: cur[ch] = {}
          cur = cur[ch]
        cur['*'] = True

      def search(self, word: str) -> bool:
        cur = self.head
        for ch in word:
          if ch not in cur: return False
          cur = cur[ch]
        return '*' in cur

      def startsWith(self, prefix: str) -> bool:
        cur = self.head
        for ch in prefix:
          if ch not in cur: return False
          cur = cur[ch]
        return True
   ```
   ```python 
    class TrieNode:
      def __init__(self):
        self.children = {}
        self.endOfWord = False
         
    class Trie:
      def __init__(self):
        self.root = TrieNode()

      def insert(self, word: str) -> None:
        cur = self.root
        for c in word:
          if c not in cur.children: cur.children[c] = TrieNode()
          cur = cur.children[c]
        cur.endOfWord = True

      def search(self, word: str) -> bool:
        cur = self.root
        for c in word:
          if c not in cur.children: return False
          cur = cur.children[c]
        return cur.endOfWord

      def startsWith(self, prefix: str) -> bool:
        cur = self.root
        for c in prefix:
          if c not in cur.children: return False
          cur = cur.children[c]
        return True
   ```
   ```
     n is the length of the word.
     Time: O(n)
     Space: O(1)
   ```

4. [**Implement Trie String Search**] Given a string `big_string` and a list of smaller strings `small_strings`, write a function that returs an array of booleans, where each item represents whether or not the corresponding item in `small_strings` exists in `big_string`.

   ```python  
    class Trie:
      def __init__(self):
        self.head = {}

      def insert(self, word):
        cur = self.head
        for ch in word:
          if ch not in cur: cur[ch] = {}
          cur = cur[ch]
        cur['*'] = word

      def search(self, word, start, containesStrings):
        cur = self.head
        for i in range(start, len(word)):
            ch = word[i]
            if ch not in cur: break
            cur = cur[ch]
            if '*' in cur: containesStrings[cur['*']] = True

    # Main function
      def multiStringSearch(big_string, small_strings):
        my_trie = Trie()
        for word in small_strings:
            my_trie.insert(word)
        containesStrings = {}
        for i, word in enumerate(big_string):
            my_trie.search(big_string, i, containesStrings)
        return [string in containesStrings for string in small_strings]
   ```
   ```
     n is the length of the word.
     Time: O(n)
     Space: O(1)
   ```

---

### Bitwise Operations

1. [**Alternating Bits**] [[**Leetcode 693**](https://leetcode.com/problems/binary-number-with-alternating-bits/)] Given a positive integer, write a function that returns a boolean indicating whether it has alternating bits (any two adjacent bits should have different values).

   ```python
   def hasAlternatingBits(n):
    while n:
      bitA = n % 2
      n >>= 1
      bitB = n % 2
      if bitA == bitB: return False
    return True
   ```

2. [**Number Complement**] [[**Leetcode 476**](https://leetcode.com/problems/number-complement/)] Given a positive integer, write a function that returns its complement. 

   ```python
   def findComplement(n):
    result = 0
    power = 1
    while nums:
      result += ((nums%2)^1) * power
      power <<= 1
      num >>= 1
    return result
   ```

3. [**Number of 1 Bits**] [[**Leetcode 191**](https://leetcode.com/problems/number-of-1-bits/)] Given an unsigned integer, write a function that returns the number of `1` bits (also known as the Hamming Weight). 

   ```python
   def hammingWeight(n):
    count = 0
    while n:
      if n%2 == 1:
        count += 1
      n >>= 1
    return count
   ```
   ```python
   def hammingWeight(n):
    count = 0
    while n:
      count += int(n & 1)
      n >>= 1
    return count
   ```
   ```python
   def hammingWeight(n):
    return Counter(bin(n)[2:])["1"]
   ```

4. [**Number of Different Bits**] [[**Leetcode 461**](https://leetcode.com/problems/hamming-distance/)] Given two integers `x` and `y`. Write a function that returns the number of positions at which the corresponding bits are different (aka the Hamming Distance). 

   ```python
   def hammingDistance(x, y):
    xor = x^y
    count = 0
    while xor:
      if xor & 1: count += 1
      xor >>= 1
    return count
   ```
   ```python
   def hammingDistance(x, y):
    count = 0
    while x or y:
        count += (x%2) ^ (y%2)
        x >>= 1
        y >>= 1
    return count
   ```
   ```python
   def hammingDistance(x, y):
    count = 0
    x = "{:032b}".format(x)
    y = "{:032b}".format(y)
    for i in range(len(x)):
        if x[i] != y[i]:
            count += 1
    return count
   ```

5. [**Add Binary**] [[**Leetcode 67**](https://leetcode.com/problems/add-binary/)] Given two binary strings `a` and `b`, write a function to return their sum as a binary string. 

   ```python
   def addBinary(a, b):
    p1, p2, carry = len(a)-1, len(b)-1, 0
    result = ""
    while (p1 >= 0) or (p2 >= 0) or carry:
      val1 = int(a[p1]) if (p1 >= 0) else 0
      val2 = int(b[p2]) if (p2 >= 0) else 0

      total = (val1+val2+carry) % 2
      carry = (val1+val2+carry) // 2
      result = str(total) + result

      p1 -= 1
      p2 -= 1
    if carry: result = '1'+result
    return result
   ```

6. [**Plus One**] [[**Leetcode 66**](https://leetcode.com/problems/plus-one/)] Given an array of integers representing a large integer where each digit is ordered from most to least significant from left-to-right, write a function to increment this integer by one and return the resulting number. 

   ```python
   def plusOne(digits):
    p1, carry = len(digits)-1, 1
    result = []
    while (p1 >= 0) or carry:
      val1 = digits[p1] if (p1 >= 0) else 0

      total = (val1 + carry) % 10
      carry = (val1 + carry) // 10
      result.insert(0, total)

      p1 -= 1
    if carry: result.insert(0, carry)
    return result
   ```

7. [**Sum of Two Integers**] [[**Leetcode 371**](https://leetcode.com/problems/sum-of-two-integers/)] Given two integers `a` and `b`, write a function to return the sum of the two integers without using the `+` and `-` operators.

   ```python
   def getSum(a, b):
    MAX = 0x7FFFFFFF # 32 bits integer max
    MIN = 0x80000000 # 32 bits interger min
    mask = 0xFFFFFFFF # mask to get last 32 bits
    while b:
      xor = (a ^ b) & mask
      carry = ((a & b) << 1) & mask
      a, b = xor, carry
    # if negative, get a's 32 bits complement
    return a if a <= MAX else ~(a ^ mask)
   ```
   ```python
   def getSum(a, b):
    return sum([a,b])
   ```

8. [**Power of Two**] [[**Leetcode 231**](https://leetcode.com/problems/power-of-two/)] Given an integer `n`, write a function to return a boolean indicating whether `n` is a power of two. 

   ```python
   def isPowerOfTwo(n):
    i = 1
    while i < n:
      i *= 2
    return i == n
   ```

9. [**Counting Bits**] [[**Leetcode 338**](https://leetcode.com/problems/counting-bits/)] Given an integer `n`, write a function that returns a list of len `n+1` where each item is the number of `1's` in the binary representation.

   ```python
   def countBits(n):
    result = []
    for i in range(n+1):
      result.append(Counter(bin(i))['1'])
    return result
   ```
   ```python
   def countBits(n):
    from collections import Counter
    result = []
    for i in range(n+1):
      result.append(Counter(bin(i))["1"])
    return result
   ```

10. [**Reverse Bits**] [[**Leetcode 190**](https://leetcode.com/problems/reverse-bits/)] Write a function to reverse the bits of a 32 bit unsigned integer and return it.

   ```python
   def reverseBits(n):
    output, bit_place = 0, 31
    while n:
      output += (n&1) << bit_place
      n >>= 1
      bit_place -= 1
    return output
   ```
   ```python
   def reverseBits(n):
    list_rep = list("{:032b}".format(n))
    list_rep.reverse()
    return int("".join(list_rep),2)
   ```

11. [**Reverse Integer**] [[**Leetcode 7**](https://leetcode.com/problems/reverse-integer/)] Given a signed 32-bit integer `n`, write a function to return the digits of `n` reversed (avoid overflow).

   ```python
   def reverse(n):
    val = abs(n)
    result = 0
    while val:
      rem = val % 10
      result = (result*10) + rem
      val //= 10
    if result > 2**31: return 0
    elif x < 0: return (-1 * result)
    else: return result
   ```
   ```python
   def reverse(x):
    is_negative = x < 0
    x = abs(x)
    result = 0
    while x:
        rem = x % 10
        result = (result*10) + rem
        x //= 10
    if result > 2**31: return 0
    return (-1*result) if is_negative else result
   ```

### Sorting Algorithms

1. [**Quick Sort**] Implement the quicksort algorithm.

   ```python
    def quickSort(nums):
      if len(nums) <= 1: return nums
      pivot = nums[len(nums)//2]
      left = [n for n in nums if n < pivot]
      mid = [n for n in nums if n == pivot]
      right = [n for n in nums if n > pivot]
      return quickSort(left) + mid + quickSort(right)
   ```

2. [**Merge Sort**] Implement the mergesort algorithm.

   ```python
    def merge_sort(nums):
      if len(nums) <= 1: return nums
      pivot = len(nums)//2
      left = merge_sort(nums[:pivot])
      right = merge_sort(nums[pivot:])
      return merge(left, right)

    def merge(l1, l2):
      result = []
      while l1 and l2:
        if l1[0] < l2[0]: result.append(l1.pop(0))
        else: result.append(l2.pop(0))
      result += l1
      result += l2
      return result
   ```
   ```python
    from collections import deque

    def merge_sort(nums):
      if len(nums) <= 1: return nums
      pivot = len(nums)//2
      left = merge_sort(nums[:pivot])
      right = merge_sort(nums[pivot:])
      return merge(left, right)


    def merge(l1, l2):
      l1, l2 = deque(l1), deque(l2)
      result = []
      while l1 and l2:
        if l1[0] < l2[0]: result.append(l1.popleft())
        else: result.append(l2.popleft())
      result += l1
      result += l2
      return result
   ```

3. [**Topological Sort**] Implement the topological sort algorithm on a DAG given as an adjacency list.

   ```python
    result=[]
    def topologicalSort(graph, root, visited=set()):
      if root not in visited:
        visited.add(root)
        for child in graph[root]:
          topologicalSort(graph, child, visited)
      result.append(root)
   ```

4. [**Tower of Hanoi**] Implement the Tower of Hanoi algorithm.

   ```python
    def hanoi(disks, source, helper, destination):
      """
      1. Move subproblem n-1 disks from source to helper
      2. Move disk n from source to destination
      3. Move subproblem n-1 disks from helper to destination
      """
      if disks == 1:
        print(f"Disk {disks} moves from tower {source} to tower {destination}.")
        return
      hanoi(disks-1, source, destination, helper)
      print(f"Disk {disks} moves from tower {source} to tower {destination}.")
      hanoi(disks-1, helper, source, destination)

    # Driver Code
    disks = int(input('Number of disks to be displaced: '))
    hanoi(disks, 'A', 'B', 'C')
   ```

### Extras

1. [**Greatest Common Divisor**] Given two numbers as arguments, Write a function that calculates the greatest common divisor (GCD).

   ```python
   def GCD(A,B):
    while B:
      if A > B:
        A = A - B
      else:
        B = B - A
    return A
   ```
   ```
     A is the first input to the function
     B is the second input to the function
     Time: O(min(A, B))
     Space: O(1)
   ```

   ```python
   def GCD(a,b):
    if b == 0: return a
    return GCD(b, a%b)
   ```
   ```
     A is the first input to the function
     B is the second input to the function
     Time: O(min(A, B))
     Space: O(min(A, B))
   ```

2. [**Lowest Common Multiple**] Given two numbers as arguments, Write a function that calculates the lowest common multiple (LCM).

   ```python
    def GCD(a,b):
      if b == 0: return a
      return GCD(b, a%b)

    def LCM(a,b):
      if a > b: return (a/gcd(a,b)) * b
      else: return (b/gcd(a,b)) * a
   ```

   ```
     A is the first input to the function
     B is the second input to the function
     Time: O(min(A, B))
     Space: O(min(A, B))
   ```

3. [**Fizz Buzz**] [[**leetcode 412**](https://leetcode.com/problems/fizz-buzz/)] Given an integer `n`, write a function to return a string array in the Fizz-Buzz pattern.

   ```python
   def fizzBuzz(n):
    answer = []
    for i in range(1, n+1):
      if (i%3 == 0) and (i%5 == 0):
        answer.append('FizzBuzz')
      elif (i%3 == 0):
        answer.append('Fizz')
      elif (i%5 == 0):
        answer.append('Buzz')
      else:
        answer.append(str(i))
    return answer
   ```

4. [**Missing Number**] [[**leetcode 268**](https://leetcode.com/problems/missing-number/)] Given an array containing `n` distinct numbers in the range `[0, n]`, write a function to return the only number missing from the range.

   ```python
   def missingNumber(nums):
    n = len(nums)
    expected_total = n*(n+1)/2
    real_total = sum(nums)
    return int(expected_total - real_total)
   ```

5. [**Robot Return to Origin**] [[**leetcode 657**](https://leetcode.com/problems/robot-return-to-origin/)] Given a robot placed at the origin `(0,0)` and a sequence of moves, write a function to return a boolean indicating whether the robot is back at the origin.

   ```python
   def judgeCircle(moves):
    x,y = 0,0
    for char in moves:
      if char == 'U': y += 1
      elif char == 'D': y -= 1
      elif char == 'R': x += 1
      elif char == 'L': x -= 1
    return (x==0) and (y==0)
   ```

6. [**Amazon Shelves**] Given a 1-indexed string to model shelves in an Amazon fufilnment center, for example `|**|*|*` where `|` represents shelf-walls and `*` represent books within the walls. This means that the string `|**|` signifies two books within that shelf. Given also a start and an end indices, write a function to return the number of valid books. A valid book must be within two walls. For example, `|**|` has 2 valid books but `|**|*` also has 2 valid books as the ending `*` is invalid because is is NOT between two shelf-walls.

   ```python
   def numberOfItems(s, start_indices, end_indices):
    output = []
    for start, end in zip(start_indices, end_indices):
      count = 0
      new_s = s[start-1: end]
      if len(new_s) < 2: continue
      new_start = new_s.index('|')
      new_end = len(new_s)-1 - new_s[::-1].index('|')
      for i in range(new_start, new_end):
        if new_s[i] == '*': count += 1
      output.append(count)
    return output
   ```

   ```python
   def numberOfItems(s, start_indices, end_indices):
    output = []
    for start, end in zip(start_indices, end_indices):
      new_s = s[start-1: end]
      if len(new_s) < 2: continue
      new_start = new_s.index('|')
      new_end = len(new_s)-1 - new_s[::-1].index('|')
      count = new_s[new_start:new_end].count('*')
      output.append(count)
    return output
   ```

7. [**Spiral Matrix**] [[**leetcode 54**](https://leetcode.com/problems/spiral-matrix/)] Given a `m x n` matrix, return all elements of the matrix in spiral order.

   ```python
   def spiralOrder(array):
    output, size = [], len(array) * len(array[0])
    left, right = 0, len(array[0])-1
    top, bottom = 0, len(array)-1
    while (len(output) < size):
      # left to right
      if (len(output) < size):
        for i in range(left, right+1): output.append(array[top][i])
        top += 1
      # top to bottom
      if (len(output) < size):
        for i in range(top, bottom+1): output.append(array[i][right])
        right -= 1
      # right to left
      if (len(output) < size):
        for i in reversed(range(left, right+1)): output.append(array[bottom][i])
        bottom -= 1
      # bottom to top
      if (len(output) < size):
        for i in reversed(range(top, bottom+1)): output.append(array[i][left])
        left += 1
    return output
   ```


---

### Tips & Tricks

1. [**Annotate Dataset**] How to quickly annotate datasets.
    - Ensure to first install the _pigeon_ module.
    `!pip install pigeon-jupyter`

    ```python
      from pigeon import annotate

      data = annotate(
          ["The food taste good.", "Very awesome resturant!", "Terrible place."],
          options=["positive", "negative"]
      )
    ```



2. [**Email Sender**] How to send email with smtp.
    - Ensure to first setup 2FA with your email provider (Gmail)

    ```python
    def sendEmail(sender, password, reciever, subject, message):
      '''Sends emails using the smtp protocol'''
      import email, ssl, smtplib
      message = email.message.EmailMessage()
      message['To'] = reciever
      message['From'] = sender
      message['Subject'] = subject
      message['Date'] = email.utils.formatdate(localtime=True)
      message['Message-ID'] = email.utils.make_msgid()
      message.set_content(body)

      context = ssl.create_default_context()
      with smtplib.SMTP_SSL('smtp.gmail.com', 465, context=context) as smtp:
        smtp.login(sender, password)
        smtp.sendmail(sender, reciever, message.as_string())

    # Driver Code
    sender, password = 'sender@gmail.com', 'sender_password'
    reciever = 'reciever@gmail.com'

    subject = 'ANNONCEMENT'
    body = '''"With great power, comes great responsibility." - Uncle Ben.'''
    sendEmail(sender, password, reciever, subject, body)
    ```

3. [**English Dictionary**] How to implement a language dictionary. 
    - Ensure to first install the _PyDictionary_ module.
      `!pip install PyDictionary`

    ```python
    def dictionary(word):
      '''Returns the meaning of the word'''
      from PyDictionary import PyDictionary
      diction = PyDictionary()
      result = diction.meaning(word)
      for key, value in result.items():
        for idx,item in enumerate(value):
          print(f"[{idx+1}] [{key}]: {item}")

    # Driver Code
    word = input("Enter a word: ")
    print(dictionary(word))
    ```

4. [**Face Detection**] How to detect faces in an image.
    - Ensure to first install the _opencv_ module.
      `!pip install opencv-python`

    ```python
    import cv2

    face_cascade_file = cv2.CascadeClassifier('/content/face_detection/haarcascade_frontalface_default.xml')
    img = cv2.imread('/content/face_detection/chris.png')
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = face_cascade_file.detectMultiScale(gray, 1.1, 4)
    # Drawing rectangle around face
    for (x, y, w, h) in faces:
      cv2.rectangle(img, (x,y), (x+w, y+h), (0, 225, 0), 2)

    cv2.imwrite("face_detected.jpg", img)
    from IPython.display import Image
    Image(filename='face_detected.jpg')
    ```


5. [**Files and Folders (using pathlib)**] Creating files and folders.
    - Both the _pathlib_ and the _calendar_ modules come with the default python installation.

    ```python
    from pathlib import Path
    import calendar

    months = list(calendar.month_name[1:])
    weeks = ['Week 1', 'Week 2', 'Week 3', 'Week 4']

    for i, month in enumerate(months, start=1):
      for week in weeks:
        Path(f"2022/{i}.{month}/{week}").mkdir(parents=True,exist_ok=True)
    ```

6. [**Files and Folders (Get Specific Files)**] How to search for specific files and folders.
    - Both the _pathlib_ modules come with the default python installation.

    ```python
    from pathlib import Path

    folder = Path('.')
    paths = folder.glob('**/*.csv')
    for path in paths:
      if path.is_file():
        print(path)
    ```

7. [**Files and Folders (Unzipping Files)**] How to zip/ unzip files.
    - Both the _pathlib_ and the _zipfile_ modules come with the default python installation.

    ```python
    from pathlib import Path
    import zipfile

    current_directory = Path('.')
    target_directory = Path('temp')

    for path in current_directory.glob('*.zip'):
        with zipfile.ZipFile(path, 'r') as zip_file:
            zip_file.extractall(path=target_directory)
    ```

8. [**Image Manipulation (Resizing)**] How to resize images.
    - The _PIL_ module should come by default. If not, use this command.
      `!pip install pillow`

    ```python
    from PIL import Image
    img = Image.open('/content/me.jpg')
    resized_img = img.resize((150, 150))
    resized_img.save('me_150.jpg')

    display(resized_img)
    ```
 
9. [**Image Manipulation (Remove Background)**] How to remove background from images.
    - The _PIL_ module should come by default. However, you need to install the _rembg_ module.
      `!pip install pillow` and `!pip install rembg`

    ```python
    from PIL import Image
    from rembg import remove
    img = Image.open('/content/me_150.jpg')
    rem_back_img = remove(img)

    display(rem_back_img)
    ```

10. [**Math to Latex Description**] How to convert equations to latex descriptions
    - The _math_ module comes with default python but the _latexify-py_ module would need to be installed.
      `!pip install latexify-py`.

    ```python
    import math
    import latexify

    @latexify.with_latex
    def solve(a,b,c):
      return (-b + math.sqrt(b**2 - 4*a*c)) / (2*a)
    solve
    ```

11. [**QR Code Generator (texts & URLs)**] How to generate QR codes for texts and URLs.
    - Ensure to install the qrcode and image modules
      `!pip install qrcode image`

    ```python
    def generateQRcode(text):
      '''returns image of a QR code'''
      qr = qrcode.QRCode(
          version=1,
          error_correction=qrcode.constants.ERROR_CORRECT_L,
          box_size=10, border=4,
      )
      qr.add_data(text)
      qr.make(fit=True)
      img = qr.make_image(fill_color="black", back_color="white")
      img.save('test.png')

    # Driver Code
    generateQRcode('https://www.youtube.com/watch?v=dQw4w9WgXcQ')
    Image(filename='test.png')
    ```


12. [**QR Code Generator (WIFI)**] How to generate QR codes for WIFI.
    - Ensure to install the wifi-qrcode-generator module
      `!pip install wifi-qrcode-generator`

    ```python
    import wifi_qrcode_generator as qr
    from IPython.display import Image
    qr.wifi_qrcode('WIFI name', False, 'WPA', 'WIFI password')
    ```

 
13. [**Schedule Functions**] How to schedule functions to run at specific time.
    - Ensure to install the schedule module
      `!pip install schedule`

    ```python
    def sayHi():
      print("Hi")
      return schedule.CancelJob

    import schedule, time
    schedule.every(3).seconds.do(sayHi)

    while True:
      schedule.run_pending()
    ```


14. [**Send Text Messages**] How to texts to be sent.
    - Ensure to use the textbelt API.

    ```python
    def sendTextMessage(msg):
      '''Sends scheduled text messages'''
      import requests
      resp = requests.post('https://textbelt.com/text', {
        'phone': '1234567890',
        'message': f'{msg}',
        'key': 'textbelt',
      })
      print(resp.json)

    # Driver Code
    msg = 'Hello world'
    sendTextMessage(msg)
    ```


15. [**Site Connectivity Checker**] How to check connectivity status of a site.
    - The _urllib_ package should come installed by default. if not, use the command
      `!pip install urllib`

    ```python
    def checkSiteConnectivity(url):
      '''Returns the status code of any url'''
      import urllib.request as request
      response = request.urlopen(url)
      return f"The connection status code is: {response.getcode()}"

    # Driver Code
    url = 'https://www.youtube.com/watch?v=dQw4w9WgXcQ&list=RDdQw4w9WgXcQ&start_radio=1'
    print(checkSiteConnectivity(url))
    ```


16. [**Timing Your Code**] How to time code execution accurately.
    - The time module should come by default. Ensure to import it.

    ```python
    import time

    # Method 1
    start = time.time()
    time.sleep(5)
    end = time.time()
    print(end - start)

    # method 2
    start = time.perf_counter()
    time.sleep(5)
    end = time.perf_counter()
    print(end - start)
    ```

17. [**Using Pipes**] How to use pipes for cleaner code.
    - Ensure to install the _pipe_ package using the command.
      `!pip install pipe`

    ```python
    from pipe import select, where

    nums = [1,2,3,4,5,6,7,8,9]
    # Without Pipes
    without_pipes = list(
        filter(lambda x: x % 2 == 0,
                map(lambda x: x ** 2, nums))
    )

    # With Pipes
    with_pipes =list(
        nums | select(lambda x: x ** 2) | where(lambda x: x % 2 == 0)
    )

    print(without_pipes)
    print(with_pipes)
    ```
