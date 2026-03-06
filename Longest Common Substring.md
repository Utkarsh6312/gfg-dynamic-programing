## 01. Longest Common Substring

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-common-substring1452/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** You are given two strings s1 and s2. Your task is to find the length of the longest common substring among the given strings.

#### Examples

##### Example 1

- **Input:**
```text
s1 = "ABCDGH", s2 = "ACDGHR"
```
- **Output:**
```text
4
```
- **Explanation:** The longest common substring is "CDGH" with a length of 4.

##### Example 2

- **Input:**
```text
s1 = "abc", s2 = "acb"
```
- **Output:**
```text
1
```
- **Explanation:** The longest common substrings are "a", "b", "c" all having length 1.

##### Example 3

- **Input:**
```text
s1 = "YZ", s2 = "yz"
```
- **Output:**
```text
0
```

#### Constraints

- **1.** `1 <= s1.size(), s2.size() <= 10³Both strings may contain upper and lower case alphabets.`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int longestCommonSubstr(string& s1, string& s2) {
        int n = s1.size();
        int m = s2.size();
        
        // dp[i][j] = length of longest common substring
        // ending at s1[i-1], s2[j-1]
        vector<vector<int>> dp(n + 1, vector<int>(m + 1, 0));
        
        int ans = 0;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                if (s1[i - 1] == s2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                    ans = max(ans, dp[i][j]);
                } else {
                    dp[i][j] = 0;  // break substring continuity
                }
            }
        }
        
        return ans;
    }
};
```

*Generated on: 3/6/2026, 4:55:59 PM*