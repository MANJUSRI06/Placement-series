# Placement Series – Take You Forward

---

### Date
**Solved On:** 28-01-2026  

---

## Problem Title
**Name:** Two Sum (Example)

---

## 📌 Problem Statement
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.
 
> Example 1:
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

> Example 2:
Input: nums = [3,2,4], target = 6
Output: [1,2]


> Example 3:
Input: nums = [3,3], target = 6
Output: [0,1]

---

## 💡 Approach / Logic

### ✔️ Brute Force
- Try all pairs
- Time: O(N²)
- Space: O(1)

### ✔️ Optimized Approach (HashMap)
- Store visited elements
- Check complement
- Time: O(N)
- Space: O(N)

solve using HashMap so loop the array first and minus the element with the target and check that res is in HashMap...if yes return the i if no move that element with index to hashmap and move to next element.

---

## 🧠 Key Observations
- Use HashMap for faster lookup
- Works only if single pair exists
- Order matters

---

## Code Implementation

### Language: Java

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int i=0; i<nums.length; i++){
            int element = target- nums[i];
            if(map.containsKey(element)){
                return new int[]{map.get(element), i};
            }
            map.put(nums[i],i);
        }
        return new int[] {};
    }
}
```

### Leetcode Link
[Two Sum](https://leetcode.com/problems/two-sum/)

### Youtube Link
[Take U Forward - Two Sum](https://www.youtube.com/watch?v=UXDSeD9mN-k)
