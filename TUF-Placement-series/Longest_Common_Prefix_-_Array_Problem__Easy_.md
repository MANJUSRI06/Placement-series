Longest Common Prefix

## Problem
Find the **longest common prefix** among an array of strings.

If no common prefix exists, return an empty string `""`.

---

## 📌 Examples

### Example 1
```text
Input: ["flower","flow","flight"]
Output: "fl"
```

### Example 2
```text
Input: ["dog","racecar","car"]
Output: ""
```

---

## 💻 Java Code

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {

        if (strs == null || strs.length == 0)
            return "";

        String prefix = strs[0];

        for (int i = 0; i < prefix.length(); i++) {

            char ch = prefix.charAt(i);

            for (int j = 1; j < strs.length; j++) {

                if (i >= strs[j].length() || strs[j].charAt(i) != ch) {
                    return prefix.substring(0, i);
                }
            }
        }

        return prefix;
    }
}
```

---

## 📖 Step-by-Step Explanation

---

### 🔹 Step 1: Check for Empty Input

```java
if (strs == null || strs.length == 0)
    return "";
```

✔ If array is empty → no prefix  
✔ Return empty string

---

### 🔹 Step 2: Use First String as Reference

```java
String prefix = strs[0];
```

✔ Take first string as base  
✔ Compare others with it

---

### 🔹 Step 3: Loop Through Characters

```java
for (int i = 0; i < prefix.length(); i++)
```

✔ `i` represents character index

---

### 🔹 Step 4: Store Current Character

```java
char ch = prefix.charAt(i);
```

✔ Store character for comparison

---

### 🔹 Step 5: Compare with Other Strings

```java
for (int j = 1; j < strs.length; j++)
```

✔ Compare remaining strings

---

### 🔹 Step 6: Stop When Mismatch Happens

```java
if (i >= strs[j].length() || strs[j].charAt(i) != ch) {
    return prefix.substring(0, i);
}
```

Stops when:

- String ends  
- Character mismatch

Returns matched prefix so far

---

### 🔹 Step 7: Return Full Prefix

```java
return prefix;
```

✔ All characters matched

---

Time: O(n × m)
Space: O(1)


# Leet Code Link: 
[Longest common Prefix](https://leetcode.com/problems/longest-common-prefix/)

