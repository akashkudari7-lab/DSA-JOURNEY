# Basic Array Operations & Beginner Programs

---

## Part 1: The 5 Fundamental Array Operations

Every data structure performs primary operations known as **CRUD** (Create, Read, Update, Delete) along with **Traversal** and **Search**.

```
              ┌─────────────────────────────────────┐
              │       Core Array Operations         │
              ├───────────┬─────────────┬───────────┤
              │ Traversal │  Searching  │ Insertion │
              ├───────────┼─────────────┼───────────┤
              │ Deletion  │   Update    │ Sorting   │
              └───────────┴─────────────┴───────────┘
```

---

### 1. Traversal (Visiting Every Element)
- **Concept:** Visiting each element of the array exactly once from index `0` to `n - 1`.
- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$

```python
# Traversal example
arr = [10, 20, 30, 40, 50]
for i in range(len(arr)):
    print(f"Index {i} -> Value {arr[i]}")
```

---

### 2. Insertion (Adding an Element)

Inserting an element requires shifting existing elements to create an empty spot:

#### A. Insert at End
- If space is available: Directly assign `arr[n] = val`.
- **Complexity:** $O(1)$

#### B. Insert at Beginning (Index 0)
- All $n$ elements must shift **one position to the right** starting from the last index.
- **Complexity:** $O(n)$

```
Original:    [ 10,  20,  30,  40,  _  ]
Shift right: [ __,  10,  20,  30,  40 ]
Insert 99:   [ 99,  10,  20,  30,  40 ]
```

#### C. Insert at Given Position (Index `pos`)
- Shift all elements from index `pos` to `n-1` one slot to the right.
- Put new element at `arr[pos]`.
- **Complexity:** $O(n)$

```python
def insert_at_index(arr: list[int], val: int, index: int) -> list[int]:
    # Manual shift implementation:
    arr.append(0)  # extend capacity by 1
    for i in range(len(arr) - 1, index, -1):
        arr[i] = arr[i - 1]
    arr[index] = val
    return arr
```

---

### 3. Deletion (Removing an Element)

Removing an element requires shifting subsequent elements **left** to fill the gap.

#### A. Delete from End
- Just decrease array logical size by 1.
- **Complexity:** $O(1)$

#### B. Delete at Index `pos`
- Shift all elements from `pos + 1` to `n - 1` **one slot to the left**.
- **Complexity:** $O(n)$

```
Original:    [ 10,  20,  30,  40,  50 ]   (Delete element 20 at index 1)
Shift left:  [ 10,  30,  40,  50,  _  ]
```

```python
def delete_at_index(arr: list[int], index: int) -> list[int]:
    # Manual shift implementation:
    for i in range(index, len(arr) - 1):
        arr[i] = arr[i + 1]
    arr.pop()  # remove last duplicate slot
    return arr
```

---

### 4. Searching

Finding the index/presence of a target value.

- **Linear Search (Unsorted Array):** Check every element from left to right.
  - **Complexity:** $O(n)$
- **Binary Search (Sorted Array):** Repeatedly divide search interval in half.
  - **Complexity:** $O(\log n)$

---

### 5. Update / Modify
- Change the value at a specific index: `arr[i] = new_value`.
- **Complexity:** $O(1)$ because memory address calculation is instantaneous.

---

## Part 2: Simple & Essential Beginner Programs

---

### Program 1: Sum and Average of an Array

```python
def calculate_sum_and_avg(arr: list[float]) -> tuple[float, float]:
    if not arr:
        return 0.0, 0.0
    
    total = 0.0
    for num in arr:
        total += num
        
    avg = total / len(arr)
    return total, avg

numbers = [12.5, 30.0, 45.5, 20.0, 10.0]
total, avg = calculate_sum_and_avg(numbers)
print(f"Sum = {total}, Average = {avg}")
# Output: Sum = 118.0, Average = 23.6
```

---

### Program 2: Find Maximum and Minimum Element

```python
def find_min_max(arr: list[int]) -> tuple[int, int]:
    if not arr:
        raise ValueError("Array cannot be empty")
        
    min_val = arr[0]
    max_val = arr[0]
    
    for i in range(1, len(arr)):
        if arr[i] < min_val:
            min_val = arr[i]
        elif arr[i] > max_val:
            max_val = arr[i]
            
    return min_val, max_val

arr = [25, 11, 7, 75, 56, 92, 3]
min_elem, max_elem = find_min_max(arr)
print(f"Smallest: {min_elem}, Largest: {max_elem}")
# Output: Smallest: 3, Largest: 92
```

---

### Program 3: Reverse an Array (In-Place Two-Pointer)

```python
def reverse_array(arr: list[int]) -> list[int]:
    left = 0
    right = len(arr) - 1
    
    while left < right:
        # Swap elements at left and right
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1
        
    return arr

arr = [1, 2, 3, 4, 5]
print("Reversed:", reverse_array(arr))
# Output: Reversed: [5, 4, 3, 2, 1]
```

---

### Program 4: Linear Search

```python
def linear_search(arr: list[int], target: int) -> int:
    for index in range(len(arr)):
        if arr[index] == target:
            return index  # Target found at index
    return -1  # Target not found

arr = [40, 10, 80, 50, 20]
target = 80
result = linear_search(arr, target)
print(f"Result index: {result}")
```

---

### Program 5: Check if Array is Sorted in Ascending Order

```python
def is_sorted(arr: list[int]) -> bool:
    for i in range(len(arr) - 1):
        if arr[i] > arr[i + 1]:
            return False  # Inversion found
    return True

print(is_sorted([10, 20, 30, 40, 50]))  # True
print(is_sorted([10, 30, 20, 40, 50]))  # False
```

---

### Program 6: Count Even and Odd Numbers

```python
def count_even_odd(arr: list[int]) -> tuple[int, int]:
    even_count = 0
    odd_count = 0
    for x in arr:
        if x % 2 == 0:
            even_count += 1
        else:
            odd_count += 1
    return even_count, odd_count

arr = [2, 7, 9, 14, 16, 21, 28]
evens, odds = count_even_odd(arr)
print(f"Evens: {evens}, Odds: {odds}")
```
