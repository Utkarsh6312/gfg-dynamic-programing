## 01. Optimal Strategy For A Game

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/optimal-strategy-for-a-game-1587115620/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** You are given an integer array arr[] of size n. The array elements represent n coins of values v_1, v_2, ....v_n. You play against an opponent in an alternating way. In each turn, a player selects either the first or last coin from the row, removes it from the row permanently, and receives the coin's value. You need to determine the maximum possible amount of money you can win if you go first.Note: Both the players are playing optimally.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [5, 3, 7, 10]
```
- **Output:**
```text
15
```
- **Explanation:** The user collects the maximum value as 15(10 + 5). It is guaranteed that we cannot get more than 15 by any possible moves.

##### Example 2

- **Input:**
```text
arr[] = [8, 15, 3, 7]
```
- **Output:**
```text
22
```
- **Explanation:** The user collects the maximum value as 22(7 + 15). It is guaranteed that we cannot get more than 22 by any possible moves.

#### Constraints

- **1.** `2 <= n <= 10³`
- **2.** `1 <= arr[i] <= 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int rec ( int i ,int j, vector<int> &a ,vector<vector<int>> &dp){
        if(i>j) return 0;
        if(dp[i][j]!=-1) return dp[i][j];
        if(i==j) return dp[i][j]=a[i];
        int l=a[i]+min(rec(i+2,j,a,dp),rec(i+1,j-1,a,dp));
        int r=a[j]+min(rec(i,j-2,a,dp),rec(i+1,j-1,a,dp));
        return dp[i][j]=max(l,r);
    }
    int maximumAmount(vector<int> &a) {
        int n=a.size();
        vector<vector<int>> dp(n,vector<int>(n,-1));
        return rec(0,a.size()-1,a,dp);
    }
};
```

*Generated on: 3/6/2026, 5:03:29 PM*