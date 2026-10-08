# LeetCode Easy: Array Problems (Curated Collection)

A step-by-step curated guide of high-frequency LeetCode Easy array problems with explanations, intuition, and optimal solutions.

---

## Table of Contents
1. [LeetCode 1: Two Sum](#1-leetcode-1-two-sum)
2. [LeetCode 26: Remove Duplicates from Sorted Array](#2-leetcode-26-remove-duplicates-from-sorted-array)
3. [LeetCode 27: Remove Element](#3-leetcode-27-remove-element)
4. [LeetCode 35: Search Insert Position](#4-leetcode-35-search-insert-position)
5. [LeetCode 66: Plus One](#5-leetcode-66-plus-one)
6. [LeetCode 88: Merge Sorted Array](#6-leetcode-88-merge-sorted-array)
7. [LeetCode 121: Best Time to Buy and Sell Stock](#7-leetcode-121-best-time-to-buy-and-sell-stock)
8. [LeetCode 136: Single Number](#8-leetcode-136-single-number)
9. [LeetCode 169: Majority Element](#9-leetcode-169-majority-element)
10. [LeetCode 217: Contains Duplicate](#10-leetcode-217-contains-duplicate)
11. [LeetCode 268: Missing Number](#11-leetcode-268-missing-number)
12. [LeetCode 283: Move Zeroes](#12-leetcode-283-move-zeroes)

---

## 1. LeetCode 1: Two Sum

### Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice.

- **Example 1:** `nums = [2, 7, 11, 15]`, `target = 9` $\rightarrow$ `[0, 1]` (2 + 7 = 9)
- **Example 2:** `nums = [3, 2, 4]`, `target = 6` $\rightarrow$ `[1, 2]`

### Intuition & Approach
- **Brute Force:** Check all pairs $(i, j)$ using two nested loops. Time: $O(n^2)$.
- **Optimal (Hash Map):** As we traverse the array, for element $x$, the required complement is $\text{target} - x$. If $\text{target} - x$ is already in our map, we found our pair! Otherwise, insert $x$ and its index into the map.

### Solution

#### Python:
```python
def twoSum(nums: list[int], target: int) -> list[int]:
    seen = {}  # value -> index
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []
```

#### C++:
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> twoSum(std::vector<int>& nums, int target) {
    std::unordered_map<int, int> seen;
    for (int i = 0; i < nums.size(); ++i) {
        int complement = target - nums[i];
        if (seen.find(complement) != seen.end()) {
            return {seen[complement], i};
        }
        seen[nums[i]] = i;
    }
    return {};
}
```

- **Time Complexity:** $O(n)$ — Single pass through the array.
- **Space Complexity:** $O(n)$ — Hash map stores up to $n$ elements.

---

## 2. LeetCode 26: Remove Duplicates from Sorted Array

### Problem Statement
Given an integer array `nums` sorted in non-decreasing order, remove duplicates **in-place** such that each unique element appears only once. Return the number of unique elements `k`.

- **Example 1:** `nums = [1, 1, 2]` $\rightarrow$ `k = 2`, `nums = [1, 2, _]`
- **Example 2:** `nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]` $\rightarrow$ `k = 5`, `nums = [0, 1, 2, 3, 4, ...]`

### Intuition & Approach
- Since the array is **sorted**, duplicates are always adjacent.
- Use **Two Pointers**:
  - `i`: points to the last unique element confirmed.
  - `j`: scans forward through the array.
  - Whenever `nums[j] != nums[i]`, increment `i` and set `nums[i] = nums[j]`.

### Solution

#### Python:
```python
def removeDuplicates(nums: list[int]) -> int:
    if not nums:
        return 0
    i = 0
    for j in range(1, len(nums)):
        if nums[j] != nums[i]:
            i += 1
            nums[i] = nums[j]
    return i + 1
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$ (In-place)

---

## 3. LeetCode 27: Remove Element

### Problem Statement
Given an integer array `nums` and an integer `val`, remove all occurrences of `val` **in-place**. Return the number of elements not equal to `val`.

- **Example 1:** `nums = [3, 2, 2, 3]`, `val = 3` $\rightarrow$ `k = 2`, `nums = [2, 2, _, _]`

### Intuition & Approach
- Maintain a pointer `k` for placing valid elements.
- Iterate with pointer `i`. If `nums[i] != val`, copy `nums[i]` to `nums[k]` and increment `k`.

### Solution

#### Python:
```python
def removeElement(nums: list[int], val: int) -> int:
    k = 0
    for i in range(len(nums)):
        if nums[i] != val:
            nums[k] = nums[i]
            k += 1
    return k
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

---

## 4. LeetCode 35: Search Insert Position

### Problem Statement
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. You must write an algorithm with $O(\log n)$ runtime.

- **Example 1:** `nums = [1, 3, 5, 6]`, `target = 5` $\rightarrow$ `2`
- **Example 2:** `nums = [1, 3, 5, 6]`, `target = 2` $\rightarrow$ `1`

### Intuition & Approach
- Standard **Binary Search**.
- If `nums[mid] == target`, return `mid`.
- If `nums[mid] < target`, search right half (`left = mid + 1`).
- If `nums[mid] > target`, search left half (`right = mid - 1`).
- If not found, the loop terminates with `left` pointing to the exact insertion index.

### Solution

#### Python:
```python
def searchInsert(nums: list[int], target: int) -> int:
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return left
```

- **Time Complexity:** $O(\log n)$
- **Space Complexity:** $O(1)$

---

## 5. LeetCode 66: Plus One

### Problem Statement
Given a large integer represented as an integer array `digits`, where each `digits[i]` is the $i$-th digit, increment the integer by one and return the resulting array of digits.

- **Example 1:** `digits = [1, 2, 3]` $\rightarrow$ `[1, 2, 4]`
- **Example 2:** `digits = [9, 9, 9]` $\rightarrow$ `[1, 0, 0, 0]`

### Intuition & Approach
- Traverse backward from the least significant digit (`digits[n - 1]`):
  - If digit $< 9$, increment by 1 and return immediately!
  - If digit $== 9$, set it to 0 and continue to the next left digit (carry propagation).
- If all digits were 9 (e.g. `[9, 9]`), the loop finishes with all 0s. Prepend `1` to get `[1, 0, 0]`.

### Solution

#### Python:
```python
def plusOne(digits: list[int]) -> list[int]:
    for i in range(len(digits) - 1, -1, -1):
        if digits[i] < 9:
            digits[i] += 1
            return digits
        digits[i] = 0
    return [1] + digits
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$ extra space (or $O(n)$ if prepending 1)

---

## 6. LeetCode 88: Merge Sorted Array

### Problem Statement
Given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`. Merge `nums2` into `nums1` as one sorted array **in-place**. `nums1` has a length of $m + n$, with the last $n$ elements set to 0.

- **Example 1:** `nums1 = [1, 2, 3, 0, 0, 0]`, `m = 3`, `nums2 = [2, 5, 6]`, `n = 3` $\rightarrow$ `[1, 2, 2, 3, 5, 6]`

### Intuition & Approach
- If we merge from the front, we would overwrite elements in `nums1`.
- **Key Insight:** Start from the **back**! Place the largest elements at index `m + n - 1` moving backward.

### Solution

#### Python:
```python
def merge(nums1: list[int], m: int, nums2: list[int], n: int) -> None:
    p1 = m - 1
    p2 = n - 1
    p = m + n - 1
    
    while p1 >= 0 and p2 >= 0:
        if nums1[p1] > nums2[p2]:
            nums1[p] = nums1[p1]
            p1 -= 1
        else:
            nums1[p] = nums2[p2]
            p2 -= 1
        p -= 1
        
    # Copy remaining elements from nums2 if any
    while p2 >= 0:
        nums1[p] = nums2[p2]
        p2 -= 1
        p -= 1
```

- **Time Complexity:** $O(m + n)$
- **Space Complexity:** $O(1)$

---

## 7. LeetCode 121: Best Time to Buy and Sell Stock

### Problem Statement
You are given an array `prices` where `prices[i]` is the price of a given stock on day $i$. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

- **Example 1:** `prices = [7, 1, 5, 3, 6, 4]` $\rightarrow$ `5` (Buy on day 2 at price 1, sell on day 5 at price 6, profit = 6 - 1 = 5)

### Intuition & Approach
- Keep track of the **minimum price seen so far**.
- At each day, calculate the potential profit: `price - min_price`.
- Update `max_profit` if current potential profit is greater.

### Solution

#### Python:
```python
def maxProfit(prices: list[int]) -> int:
    min_price = float('inf')
    max_profit = 0
    
    for price in prices:
        if price < min_price:
            min_price = price
        elif price - min_price > max_profit:
            max_profit = price - min_price
            
    return max_profit
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

---

## 8. LeetCode 136: Single Number

### Problem Statement
Given a non-empty array of integers `nums`, every element appears twice except for one. Find that single one. You must implement a solution with a linear runtime complexity and use only constant extra space.

- **Example 1:** `nums = [2, 2, 1]` $\rightarrow$ `1`
- **Example 2:** `nums = [4, 1, 2, 1, 2]` $\rightarrow$ `4`

### Intuition & Approach
- Use the **Bitwise XOR ($\oplus$)** operator properties:
  1. $a \oplus a = 0$ (Any number XORed with itself is 0)
  2. $a \oplus 0 = a$
  3. XOR is commutative and associative.
- XORing all elements together cancels out all pairs, leaving only the single number!

### Solution

#### Python:
```python
def singleNumber(nums: list[int]) -> int:
    result = 0
    for num in nums:
        result ^= num
    return result
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

---

## 9. LeetCode 169: Majority Element

### Problem Statement
Given an array `nums` of size $n$, return the majority element. The majority element is the element that appears more than $\lfloor n / 2 \rfloor$ times.

- **Example 1:** `nums = [3, 2, 3]` $\rightarrow$ `3`
- **Example 2:** `nums = [2, 2, 1, 1, 1, 2, 2]` $\rightarrow$ `2`

### Intuition & Approach
- **Boyer-Moore Voting Algorithm:**
  - Maintain a `candidate` and a `count`.
  - When `count == 0`, assign current number as `candidate`.
  - If current number == `candidate`, increment `count`. Else decrement `count`.
  - The majority element will always survive because it appears $> n/2$ times.

### Solution

#### Python:
```python
def majorityElement(nums: list[int]) -> int:
    candidate = None
    count = 0
    
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
        
    return candidate
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

---

## 10. LeetCode 217: Contains Duplicate

### Problem Statement
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

- **Example 1:** `nums = [1, 2, 3, 1]` $\rightarrow$ `true`
- **Example 2:** `nums = [1, 2, 3, 4]` $\rightarrow$ `false`

### Intuition & Approach
- Use a **Hash Set**. As we iterate through `nums`, check if current number is already in the set:
  - If yes $\rightarrow$ duplicate found, return `true`.
  - If no $\rightarrow$ add to set.
- If loop ends $\rightarrow$ all elements are unique, return `false`.

### Solution

#### Python:
```python
def containsDuplicate(nums: list[int]) -> bool:
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(n)$

---

## 11. LeetCode 268: Missing Number

### Problem Statement
Given an array `nums` containing $n$ distinct numbers in the range $[0, n]$, return the only number in the range that is missing from the array.

- **Example 1:** `nums = [3, 0, 1]` $\rightarrow$ `2` (range is [0, 3], missing 2)
- **Example 2:** `nums = [0, 1]` $\rightarrow$ `2`

### Intuition & Approach
- **Mathematical Formula:** The sum of numbers from $0$ to $n$ is:
  $$\text{Expected Sum} = \frac{n \times (n + 1)}{2}$$
- Subtract the actual array sum from $\text{Expected Sum}$. The difference is the missing number!

### Solution

#### Python:
```python
def missingNumber(nums: list[int]) -> int:
    n = len(nums)
    expected_sum = n * (n + 1) // 2
    actual_sum = sum(nums)
    return expected_sum - actual_sum
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

---

## 12. LeetCode 283: Move Zeroes

### Problem Statement
Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements. You must do this **in-place**.

- **Example 1:** `nums = [0, 1, 0, 3, 12]` $\rightarrow$ `[1, 3, 12, 0, 0]`

### Intuition & Approach
- **Two Pointers:**
  - `last_non_zero`: points to where the next non-zero number should go.
  - Iterate through array with `curr`. When `nums[curr] != 0`, swap `nums[last_non_zero]` with `nums[curr]` and increment `last_non_zero`.

### Solution

#### Python:
```python
def moveZeroes(nums: list[int]) -> None:
    last_non_zero = 0
    for curr in range(len(nums)):
        if nums[curr] != 0:
            nums[last_non_zero], nums[curr] = nums[curr], nums[last_non_zero]
            last_non_zero += 1
```

- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$
