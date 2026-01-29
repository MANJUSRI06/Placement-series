# Placement Series – Take You Forward

---

### Date
**Solved On:** 29-01-2026  

---

## Problem Title
**Name:** Reverse Pairs (Hard Problem)

---

## 📌 Problem Statement
Given an integer array `nums`, return the number of **reverse pairs**.

A reverse pair is a pair `(i, j)` such that:

- `0 ≤ i < j < nums.length`
- `nums[i] > 2 * nums[j]`

> Example 1:  
Input: nums = [1,3,2,3,1]  
Output: 2  

Explanation:  
(1,4) → 3 > 2×1  
(3,4) → 3 > 2×1  

> Example 2:  
Input: nums = [2,4,3,5,1]  
Output: 3  

---

## 💡 Approach / Logic

### ✔️ Brute Force
- Check all possible pairs
- Use nested loops
- Compare nums[i] > 2*nums[j]

**Time:** O(N²) ❌  
**Space:** O(1)

⚠️ Issue:  
- Causes TLE for large inputs  
- Integer overflow possible

---

### ✔️ Optimized Approach (Merge Sort)

- Use Modified Merge Sort
- Divide array into halves
- Count reverse pairs while merging
- Use two pointers

**Time:** O(N log N) ✅  
**Space:** O(N)

---

## 🧠 Key Observations

- Brute force is too slow for large N
- Multiplication may overflow → use `long`
- Sorted halves help in counting pairs
- Two pointer technique improves speed

---

## Code Implementation

### Language: Java

```java
class Solution {

    public int reversePairs(int[] nums) {
        return mergeSort(nums, 0, nums.length - 1);
    }

    private int mergeSort(int[] nums, int left, int right) {

        if (left >= right) return 0;

        int mid = left + (right - left) / 2;
        int count = 0;

        count += mergeSort(nums, left, mid);
        count += mergeSort(nums, mid + 1, right);

        count += countPairs(nums, left, mid, right);

        merge(nums, left, mid, right);

        return count;
    }

    private int countPairs(int[] nums, int left, int mid, int right) {

        int count = 0;
        int j = mid + 1;

        for (int i = left; i <= mid; i++) {

            while (j <= right && (long) nums[i] > 2L * nums[j]) {
                j++;
            }

            count += (j - (mid + 1));
        }

        return count;
    }

    private void merge(int[] nums, int left, int mid, int right) {

        int[] temp = new int[right - left + 1];

        int i = left, j = mid + 1, k = 0;

        while (i <= mid && j <= right) {

            if (nums[i] <= nums[j]) {
                temp[k++] = nums[i++];
            } else {
                temp[k++] = nums[j++];
            }
        }

        while (i <= mid) temp[k++] = nums[i++];
        while (j <= right) temp[k++] = nums[j++];

        for (int p = 0; p < temp.length; p++) {
            nums[left + p] = temp[p];
        }
    }
}
```

### Complexity Analysis

Time:	O(N log N)
Space:	O(N)


### Leetcode Link
[Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)

### Youtube Link
[Take U Forward - Reverse pairs](https://www.youtube.com/watch?v=0e4bZaP3MDI)
