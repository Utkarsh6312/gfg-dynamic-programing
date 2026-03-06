## 01. Longest Palindrome in a String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-palindrome-in-a-string3411/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given a string s, your task is to find the longest palindromic substring within s.
A substring is a contiguous sequence of characters within a string, defined as s[i...j] where 0 ≤ i ≤ j < len(s).
A palindrome is a string that reads the same forward and backward. More formally, s is a palindrome if reverse(s) = = s.

> **Note:** If there are multiple palindromic substrings with the same length, return the first occurrence of the longest palindromic substring from left to right.

#### Examples

##### Example 1

- **Input:**
```text
s = “forgeeksskeegfor”
```
- **Output:**
```text
“geeksskeeg”
```
- **Explanation:** There are several possible palindromic substrings like “kssk”, “ss”, “eeksskee” etc. But the substring “geeksskeeg” is the longest among all.

##### Example 2

- **Input:**
```text
s = “Geeks”
```
- **Output:**
```text
“ee”
```
- **Explanation:** "ee" is the longest palindromic substring of "Geeks".

##### Example 3

- **Input:**
```text
s = “abc”
```
- **Output:**
```text
“a”
```
- **Explanation:** "a", "b" and "c" are longest palindromic substrings of same length. So, the first occurrence is returned.

#### Constraints

- **1.** `1 ≤ s.size() ≤ 10³s consist of only lowercase English letters.`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    string longestPalindrome(string &a) {
        // code here
        int n=a.size();
        int c=0,m=0,p=-1,l,r;
        // string s="";
        for(int i=1;i<n-1;i++){
            c=0;
            if(a[i]==a[i-1]){
                c=2;
                l=i-2;r=i+1;
                while(l>=0 && r<n){
                    if(a[l]==a[r]){
                        c+=2;l--;r++;
                    }else break;
                }
                if(c>m){
                    m=c,p=l+1;
                }
                
            }
            if(a[i-1]==a[i+1]){
                c=3;
                l=i-2;r=i+2;
                while(l>=0 && r<n){
                    if(a[l]==a[r]){
                        c+=2;l--;r++;
                    }else break;
                }
                if(c>m){
                    m=c,p=l+1;
                }
            }
        }return a.substr(p,m);
    }
};
```

*Generated on: 3/6/2026, 4:55:41 PM*