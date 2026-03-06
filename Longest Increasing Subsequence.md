## 01. Longest Increasing Subsequence

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-increasing-subsequence-1587115620/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an array arr[] of non-negative integers, the task is to find the length of the Longest Strictly Increasing Subsequence (LIS).A subsequence is strictly increasing if each element in the subsequence is strictly less than the next element.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [5, 8, 3, 7, 9, 1]
```
- **Output:**
```text
3
```
- **Explanation:** The longest strictly increasing subsequence could be [5, 7, 9], which has a length of 3.

##### Example 2

- **Input:**
```text
arr[] = [10, 6, 3, 11, 7, 15]
```
- **Output:**
```text
3
```
- **Explanation:** One of the possible longest strictly increasing subsequences is [10, 11, 15], which has a length of 3.

##### Example 3

- **Input:**
```text
arr[] = [3, 10, 2, 1, 20]
```
- **Output:**
```text
3
```
- **Explanation:** The longest strictly increasing subsequence could be [3, 10, 20], which has a length of 3.

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10³`
- **2.** `0 ≤ arr[i] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int rec(int i,int j,vector<int>& a,vector<vector<int>> &dp,int n){
        if(i>=n){
            return 0;
        }
        if(dp[i][j+1]!=-1)  return dp[i][j+1];
        int t=INT_MIN; 
        if(j==-1 || a[i]>a[j]){
            t=1+rec(i+1,i,a,dp,n);
        }
        int nt=rec(i+1,j,a,dp,n);
        return dp[i][j+1]=max(t,nt);
    }
    int lis(vector<int>& a) {
        int n=a.size();
        vector<vector<int>> dp(n,(vector<int> (n,-1)));
        return rec(0,-1,a,dp,n);
    }
};
```

*Generated on: 3/6/2026, 4:55:24 PM*