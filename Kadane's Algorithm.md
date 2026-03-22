## 01. Kadane's Algorithm

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1?page=1&category=Dynamic%20Programming&sortBy=submissions)

### Problem Description

**Task:** You are given an integer array arr[]. You need to find the maximum sum of a subarray (containing at least one element) in the array arr[].

> **Note:** A subarray is a continuous part of an array.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [2, 3, -8, 7, -1, 2, 3]
```
- **Output:**
```text
11
```
- **Explanation:** The subarray [7, -1, 2, 3] has the largest sum 11.

##### Example 2

- **Input:**
```text
arr[] = [-2, -4]
```
- **Output:**
```text
-2
```
- **Explanation:** The subarray [-2] has the largest sum -2.

##### Example 3

- **Input:**
```text
arr[] = [5, 4, 1, 7, 8]
```
- **Output:**
```text
25
```
- **Explanation:** The subarray [5, 4, 1, 7, 8] has the largest sum 25.

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁵-10⁴ ≤ arr[i] ≤ 10⁴`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-03-12 20:45:30
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int maxSubarraySum(vector<int> &a) {
        // Code here
        int  n=a.size();
        int s=a[0],m=a[0];
        // ye har pasition me us no tak ka maximum subarray store karta hai
        // yaha max wala game chalta hai
        for(int i=1;i<n;i++){
            int x=a[i];
            s=max(a[i],a[i]+s);
            // max( current array , jo abhi tak sum calculate kar rhe)
            m=max(m,s);
        }
        return m;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2025-09-24 15:43:44
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int maxSubarraySum(vector<int> &a) {
        // Code here
        int  n=a.size();
        int s=a[0],m=a[0];
        for(int i=1;i<n;i++){
            int x=a[i];
            s=max(a[i],a[i]+s);
            m=max(m,s);
        }
        return m;
    }
};
```

*Generated on: 3/12/2026, 8:46:13 PM*
