## 01. Subset Sum Problem

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an array of positive integers arr[] and a value sum, determine if there is a subset of arr[] with sum equal to given sum.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [3, 34, 4, 12, 5, 2], sum = 9Output: true
```
- **Explanation:** Here there exists a subset with target sum = 9, 4+3+2 = 9.

##### Example 2

- **Input:**
```text
arr[] = [3, 34, 4, 12, 5, 2], sum = 30
```
- **Output:**
```text
false
```
- **Explanation:** There is no subset with target sum 30.

##### Example 3

- **Input:**
```text
arr[] = [1, 2, 3], sum = 6
```
- **Output:**
```text
trueExplanation: The entire array can be taken as a subset, giving 1 + 2 + 3 = 6.
```

#### Constraints

- **1.** `1 <= arr.size() <=`
- **2.** `2001<= arr[i] <=`
- **3.** `2001<= sum <= 10<sup>4</sup>`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(sum*n)
- **Expected Auxiliary Space Complexity:** O(sum)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
  
    vector<vector<int>> dp; // -1 = uncomputed, 0 = false, 1 = true

    int rec(int ci, int cs, vector<int>& a, int x) {
        // If we already reached the target sum, success
        if (cs == x) return 1;

        // Out of bounds or sum exceeded -> fail
        if (ci >= (int)a.size() || cs > x) return 0;

        int &res = dp[ci][cs];
        if (res != -1) return res;

        // Option 1: take current element
        int take = rec(ci + 1, cs + a[ci], a, x);

        // Option 2: skip current element
        int notTake = rec(ci + 1, cs, a, x);

        // We only care if any path works (boolean OR)
        return res = (take || notTake);
    }

    bool isSubsetSum(vector<int>& a, int x) {
        int n = a.size();
        dp.assign(n, vector<int>(x + 1, -1));  // dp[n][x+1]
        return rec(0, 0, a, x);
    }
};
```

*Generated on: 3/6/2026, 4:06:36 PM*
