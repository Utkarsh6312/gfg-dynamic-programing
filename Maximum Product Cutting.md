## 01. Maximum Product Cutting

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-product-cutting4522/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given a rope of length N meters, cut the rope in different parts of integer lengths in a way that maximizes the product of lengths of all parts. You must make at least one cut. Assume that the length of the rope is more than one meter.
Example 1:

#### Examples

##### Example 1

- **Input:**
```text
N = 5
```
- **Output:**
```text
6
```
- **Explanation:** Maximum obtainable product is 2*3 Example 2:

##### Example 2

- **Input:**
```text
N = 2
```
- **Output:**
```text
1
```
- **Explanation:** Maximum obtainable product is 1*1 Your Task: You don't need to read input or print anything. Complete the function maxProduct() which takes N as input parameter and returns the maximum product.Expected Time Complexity: O(N^2)Expected Auxiliary Space: O(N)Constraints:2 ≤ N ≤ 50

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** Not found
- **Expected Auxiliary Space Complexity:** Not found

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int maxProduct(int n) {

        // Your code goes here
        vector<long long> dp(n + 1, 0);

        if (n >= 1) dp[1] = 1;   // IMPORTANT: handle n=1 as per GFG
        if (n >= 2) dp[2] = 1;   // 1*1

        for (int i = 3; i <= n; i++) {
            long long best = 0;
            for (int j = 1; j < i; j++) {
                best = max(best, max(1LL * j * (i - j), 1LL * j * dp[i - j]));
            }
            dp[i] = best;
        }
        return dp[n];
    }
};
```

*Generated on: 3/6/2026, 5:08:43 PM*