# DataStructuresAlgorithm_Master

In this repo we explore data structures and algorithms in depth. Please enjoy!

### Table Of Content

- [Arrays & Strings](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#arrays--strings)
- [Linked Lists](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#linked-lists)
- [Binary Trees](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#binary-trees)
- [Stacks](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#stacks)
- [Dynamic Programming](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#dynamic-programming)
- [Extras](https://github.com/ccibeekeoc42/DataStructuresAlgorithm_Master#extras)

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

5. [**Reverse String**] Write a function that takes in a list of strings and returns the reverse of the list of strings. For example, if the input is `[hello]` it'll return `[olleh]`.

   ```python
   def reverseString(s):
    l,r = 0,len(s)-1
    while l < r:
      s[l], s[r] = s[r], s[l]
      l += 1
      r -= 1
    return s
   ```

   ```
     n is the length of s
     Time: O(n)
     Space: O(1)
   ```

6. [**Anagrams**] Write a function that takes in two strings and returns a boolean indicating whether both strings are anagrams or not. For example, the strings `monkeyswrite` and `newyorktimes` are anagrams so the function should return `True`.

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

7. [**First Unique Character**] Write a function that takes a string and returns the index of the first unique character in the string.

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

8. [**Contains Duplicates**] Write a function that takes in a list of numbers and returns `True` if the list contains a duplicate and `False` otherwise.

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
   def containsDuplicate2(nums):
    memo = set(nums)
    return len(memo) != len(nums)
   ```

   ```
     n is the length of the list
     Time: O(n)
     Space:O(n)

   ```

9. [**Contains Duplicates II**] Write a function that takes in a list of numbers and a constant `k` and returns `True` if the list contains a set duplicates whose indicies are also at most `k` distance but returns `False` otherwise.

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

10. [**Find Duplicates**] Write a function that takes a list of numbers and returns a list containing all the duplicates (occurs exactly twice) in the input list.

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

11. [**Most Frequent Character**] Write a function that takes a string and returns the most frequent character in that string and its number of occurance. For example, the string `mississippi` has the most frequent character `i` or `s` and they both occur `4` times.

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

12. [**Two Sum**] Write a function that takes a list and a target sum and returns a pair of unique indices of numbers that add up to the target sum.

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

13. [**Two Prod**] Write a function that takes a list and a target product and returns a pair of unique indices of numbers that multiply up to the target product.

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

14. [**Intersection**] Write a function that takes in two lists and returns a new list containing elements that are in both lists.

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

15. [**Move Zeros**] Write a function that takes a list of numbers and rearranges the elements such that 0s appear at the end. This should be done inplace without creating a new list.

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

#### Linked Lists

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
    for items in values:
      cur.next = Node(items)
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

14. [**Reverse List**] Given the head of a linked list like `a->b->c->d->e`. Write a function that reverses the order of the nodes in the list. The example above should return `e->d->c->b->a`.

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

15. [**Remove Duplicates**] Given the head of a linked list like `a->b->b->c->d->d->e`. Write a function that returns the list but with each item occuring only once. The example above should return `a->b->c->d->e`.

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

17. [**Merge List**] Given the heads of two sorted linked lists `1->2->6->10` and `3->7->8->12`. Write a function that returns a single sorted linked list from the two inpute lists. The example above should return `1->2->3->6->7->8->10->12`.

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

20. [**Remove Node**] Given the head of a linked list like `3->3->9->` and a node value to delete like `9`. Write a function that deletes the first occuring node with that value. The example above should return `3->3->`.

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

21. [**Remove Nodes**] Given the head of a linked list like `3->9->3->9->` and a node value to delete like `9`. Write a function that deletes all ocurrance of the nodes with that value. The example above should return `3->3->`.

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

22. [**Insert Node**] Given the head of a linked list like `3->3->9->`, a value like `6` and and index like `2`. Write a function that insertes the given value in the specified index of the linked list. The example above should return `3->3->6->9`.

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

23. [**Add Lists**] Given the heads of two linked lists (with each list representing a number written in the reverse order. For example the numbers `621` and `354` would be given as `1->2->6` and `4->5->3`. Write a function that returns the head of a new linked list representing the sum of both input lists. The example above would result in `5->7->9` which is `975`.

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
      val1 = cur1.val if cur1 else 0
      val2 = cur2.val if cur2 else 0

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

#### Binary Tree

1. [**Depth First Values**] Given the root of a binary tree, write a function to print all values in the tree using a depth first search approach (dfs).

   ```python
   def depthFirstValues(root):
     '''Iterative Approach'''
     s = [root]
     while s:
       cur = s.pop()
       print(cur.val, end=",")
       if cur.right: s.append(cur.right)
       if cur.left: s.append(cur.left)
     return res
   ```

   ```python
   def depthFirstValues(root):
   '''Recursieve Approach'''
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

2. [**Depth First List**] Given the root of a binary tree, write a function to return a list of all values in the tree using a depth first search approach (dfs).

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

3. [**Breadth First List**] Given the root of a binary tree, write a function to return a list of all values in the tree using a depth first search approach (dfs).

   ```python
   def depthFirstValues(root):
    '''Iterative Approach'''
     if not root: return []
     res = []
     q = [root]
     while s:
       cur = s.pop(0)
       res.append(cur.val)
       if cur.left: s.append(cur.left)
       if cur.right: s.append(cur.right)
     return res
   ```

   ```
   n is the number of nodes
   Time: O(n)
   Space: O(n)
   ```

---

#### Stacks

1. [**Remove Consecutive Duplicates**] Given a string, return a string where ll consecutive duplicates have been removed. Example, for the input string `abbccwaabba` the function would return `awa`.

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

#### Extras

1. [**Greatest Common Divisor**] Given two numbers as arguments, Write a function that calculates the greatest common divisor (GCD) also known as the lowest common multiple (LCM).

   ```python
   def GCD(A,B):
    while:
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
