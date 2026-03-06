## 01. Edit Distance

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/edit-distance3702/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given two strings s1 and s2. Return the minimum number of operations required to convert s1 to s2.The possible operations are permitted:
Insert a character at any position of the string.
Remove any character from the string.
Replace any character from the string with any other character.

#### Examples

##### Example 1

- **Input:**
```text
s1 = "geek", s2 = "gesek"
```
- **Output:**
```text
1
```
- **Explanation:** One operation is required, inserting 's' between two 'e' in s1.

##### Example 2

- **Input:**
```text
s1 = "gfg", s2 = "gfg"
```
- **Output:**
```text
0
```
- **Explanation:** Both strings are same.

##### Example 3

- **Input:**
```text
s1 = "abcd", s2 = "bcfe"
```
- **Output:**
```text
3
```
- **Explanation:** We can convert s1 into s2 by removing ‘a’, replacing ‘d’ with ‘f’ and inserting ‘e’ at the end.

#### Constraints

- **1.** `1 ≤ s1.length(), s2.length() ≤ 10³Both the strings are in lowercase.`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    // Levenshtein edit distance (optimized to O(min(n,m)) space)
    int editDistance(string& s1, string& s2) {
        int n = (int)s1.size(), m = (int)s2.size();
        if (n == 0) return m;
        if (m == 0) return n;

        // ensure m <= n to use O(m) space (optional)
        if (m > n) {
            // swap to keep second string the shorter one for less space
            return editDistance(s2, s1);
        }

        vector<int> prev(m+1), cur(m+1);
        for (int j = 0; j <= m; ++j) prev[j] = j; // turning empty s1 -> s2 prefix

        for (int i = 1; i <= n; ++i) {
            cur[0] = i; // turning s1[0..i-1] -> empty s2: i deletions
            for (int j = 1; j <= m; ++j) {
                if (s1[i-1] == s2[j-1]) {
                    cur[j] = prev[j-1];
                } else {
                    int del = prev[j];      // delete s1[i-1]
                    int ins = cur[j-1];    // insert s2[j-1]
                    int rep = prev[j-1];   // replace
                    cur[j] = 1 + min(del, min(ins, rep));
                }
            }
            prev.swap(cur);
        }
        return prev[m];
    }
};
```

*Generated on: 3/6/2026, 5:02:37 PM*