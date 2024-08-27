
# Python Sorting Algorithms

This repository contains Python implementations of various fundamental sorting algorithms. Each algorithm is described with its time and space complexities, followed by the code implementation in Python.

---

## Quick Sort

**Quick Sort** is an efficient, in-place, divide-and-conquer sorting algorithm. It selects a pivot element from the array and partitions the other elements into two sub-arrays according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

- **Time Complexity:** 
  - Best Case: O(n log n)
  - Average Case: O(n log n)
  - Worst Case: O(n²)
- **Space Complexity:** O(log n) (due to recursion stack)

### Implementation:

```python
def q_sort(nums):
    n = len(nums)
    
    if n <= 1:
        return nums
    else:
        pivot = nums.pop()
        
    greater = []
    lesser = []
    
    for i in nums:
        if i > pivot:
            greater.append(i)
        else:
            lesser.append(i)
            
    return q_sort(lesser) + [pivot] + q_sort(greater)
    
print("Quick Sort:", q_sort([5, 2, 3, 8, 4, 6])) 
```

---

## Selection Sort

**Selection Sort** is a simple comparison-based algorithm. It repeatedly selects the smallest (or largest, depending on the sorting order) element from the unsorted portion and moves it to the end of the sorted portion. Although easy to understand and implement, it is not suitable for large datasets.

- **Time Complexity:** O(n²) for all cases
- **Space Complexity:** O(1) (in-place sorting)

### Implementation:

```python
def s_sort(nums):
    for i in range(len(nums)):
        mini = i
        for j in range(i + 1, len(nums)):
            if nums[j] < nums[mini]:
                mini = j
        nums[i], nums[mini] = nums[mini], nums[i]
    return nums
    
print("Selection Sort:", s_sort([5, 2, 3, 8, 4, 6]))

```

---

## Bubble Sort

**Bubble Sort** is a basic sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted. While Bubble Sort is simple to understand and implement, it is inefficient for large datasets.

- **Time Complexity:**
  - Best Case: O(n)
  - Average Case: O(n²)
  - Worst Case: O(n²)
- **Space Complexity:** O(1) (in-place sorting)

### Implementation:

```python
def b_sort(nums):
    for i in range(len(nums) - 1, 0, -1):
        for j in range(i):
            if nums[j] > nums[j + 1]:
                nums[j], nums[j + 1] = nums[j + 1], nums[j]
    return nums
    
print("Bubble Sort:", b_sort([5, 2, 3, 8, 4, 6]))
```

---

## Merge Sort

**Merge Sort** is a stable, divide-and-conquer sorting algorithm. It divides the input array into two halves, recursively sorts each half, and then merges the two sorted halves to produce the final sorted array. Merge Sort is known for its efficiency and guarantees a time complexity of O(n log n), making it suitable for large datasets.

- **Time Complexity:**
  - Best Case: O(n log n)
  - Average Case: O(n log n)
  - Worst Case: O(n log n)
- **Space Complexity:** O(n) (due to auxiliary arrays used during merging)

### Implementation:

```python
def m_sort(nums):
    n = len(nums)
    
    if n == 1:
        return nums
        
    mid = n // 2
    
    left = m_sort(nums[:mid])
    right = m_sort(nums[mid:])
    
    return merge(left, right)

def merge(left, right):
    sort = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sort.append(left[i])
            i += 1
        else:
            sort.append(right[j])
            j += 1
            
    sort.extend(left[i:])
    sort.extend(right[j:])
        
    return sort
            
print("Merge Sort:", m_sort([5, 2, 3, 8, 4, 6]))
```

---
