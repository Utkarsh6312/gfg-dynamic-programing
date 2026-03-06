## 01. Stickler Thief

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/stickler-theif-1587115621/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Stickler the thief wants to loot money from the houses arranged in a line. He cannot loot two consecutive houses and aims to maximize his total loot.Given an array, arr[] where arr[i] represents the amount of money in the i-th house. Determine the maximum amount he can loot.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [6, 7, 1, 3, 8, 2, 4]
```
- **Output:**
```text
19
```
- **Explanation:** Maximum amount he can get by looting 1st, 3rd, 5th and 7th house, which is 6 + 1 + 8 + 4 = 19.

##### Example 2

- **Input:**
```text
arr[] = [5, 3, 4, 11, 2]
```
- **Output:**
```text
16
```
- **Explanation:** Maximum amount he can get by looting 1st and 4th house, which is 5 + 11 = 16.

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁵`
- **2.** `1 ≤ arr[i] ≤ 10⁴`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int findMaxSum(vector<int>& a) {
        // code here
        int n=a.size();
        if(n==0)return 0;
        if(n==1)return a[0];
        
        int p2=a[0];
        int p1=max(a[1],a[0]);
        for(int i=2;i<a.size();i++){
            int c=max(p1,p2+a[i]);
            p2=p1;
            p1=c;
        }return p1;
    }
};
```

*Generated on: 3/6/2026, 5:02:22 PM*