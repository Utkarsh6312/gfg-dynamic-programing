## 01. Coin Change (Count Ways)

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/coin-change2448/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an integer array coins[ ] representing different denominations of currency and an integer sum, find the number of ways you can make sum by using different combinations from coins[ ]. Note: Assume that you have an infinite supply of each type of coin. Therefore, you can use any coin as many times as you want.Answers are guaranteed to fit into a 32-bit integer.

#### Examples

##### Example 1

- **Input:**
```text
coins[] = [1, 2, 3], sum = 4
```
- **Output:**
```text
4
```
- **Explanation:** Four Possible ways are: [1, 1, 1, 1], [1, 1, 2], [2, 2], [1, 3].

##### Example 2

- **Input:**
```text
coins[] = [2, 5, 3, 6], sum = 10
```
- **Output:**
```text
5
```
- **Explanation:** Five Possible ways are: [2, 2, 2, 2, 2], [2, 2, 3, 3], [2, 2, 6], [2, 3, 5] and [5, 5].

##### Example 3

- **Input:**
```text
coins[] = [5, 10], sum = 3
```
- **Output:**
```text
0Explanation: Since all coin denominations are greater than sum, no combination can make the target sum.
```

#### Constraints

- **1.** `1 <= sum <= 10³`
- **2.** `1 <= coins[i] <= 10⁴^1 <= coins.size() <= 10³`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * sum)
- **Expected Auxiliary Space Complexity:** O(sum)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    vector<vector<long long>> dp;

    long long rec(int i, int s, vector<int> &c) {
        // base: exact sum formed
        if (s == 0) return 1;

        // base: no coins left or sum negative
        if (i >= (int)c.size() || s < 0) return 0;

        // already computed
        if (dp[i][s] != -1) return dp[i][s];

        // take current coin (unbounded → stay at i)
        long long take = rec(i, s - c[i], c);

        // don’t take current coin → move to i+1
        long long notTake = rec(i + 1, s, c);

        return dp[i][s] = take + notTake;
    }

    int count(vector<int>& coins, int sum) {
        int n = coins.size();
        dp.assign(n, vector<long long>(sum + 1, -1));
        return (int)rec(0, sum, coins);
    }
};
```

*Generated on: 3/6/2026, 5:01:04 PM*