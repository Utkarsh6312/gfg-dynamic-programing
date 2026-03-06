## 01. Count all possible paths from top left to bottom right

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-all-possible-paths-from-top-left-to-bottom-right3011/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** The task is to count all the possible paths from top left to bottom right of a m X n matrix with the constraints that from each cell you can either move only to right or down.Examples :

#### Examples

##### Example 1

- **Input:**
```text
m = 2, n = 2
```
- **Output:**
```text
2
```
- **Explanation:** Two possible ways are RD and DR.

##### Example 2

- **Input:**
```text
m = 3, n = 3
```
- **Output:**
```text
6
```
- **Explanation:** Six possible ways are RRDD, DDRR, RDDR, DRRD, RDRD, DRDR.

#### Constraints

- **1.** `1 <= m <= 17`
- **2.** `1 <= n <= 17`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(m*n)
- **Expected Auxiliary Space Complexity:** O(m*n)

### Code (C++)

**Language:** `C++`

```cpp
// User function Template for C++
class Solution {
  public:
    int cP(int i,int j,int m,int n,vector<vector<int>>& dp){
        if(i==m-1 && j==n-1)return 1;
        if (i>=m || j>=n) return 0;
        if(dp[i][j]!=-1)return dp[i][j];
        return dp[i][j]=cP(i+1,j,m,n,dp)+cP(i,j+1,m,n,dp);
    }
    int numberOfPaths(int m, int n) {
        // code here
        vector<vector<int>> dp(m,vector<int>(n,-1));
        return cP(0,0,m,n,dp);
    }
};
```

*Generated on: 3/6/2026, 5:04:03 PM*