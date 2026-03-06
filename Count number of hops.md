## 01. Count number of hops

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-number-of-hops-1587115620/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** A frog jumps either 1, 2, or 3 steps to go to the top. In how many ways can it reach the top of nth step.

#### Examples

##### Example 1

- **Input:**
```text
n = 4
```
- **Output:**
```text
7
```
- **Explanation:** Below are the 7 ways to reach 4th step: 1 step + 1 step + 1 step + 1 step 1 step + 2 step + 1 step 2 step + 1 step + 1 step 1 step + 1 step + 2 step 2 step + 2 step 3 step + 1 step 1 step + 3 step

##### Example 2

- **Input:**
```text
n = 2
```
- **Output:**
```text
2
```
- **Explanation:** Below are the 2 ways to reach 2nd step: 1 step + 1 step 2 step

##### Example 3

- **Input:**
```text
n = 1
```
- **Output:**
```text
1
```

#### Constraints

- **1.** `1 ≤ n ≤ 30`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp

class Solution {
  public:
    // Function to count the number of ways in which frog can reach the top.
    int countWays(int n) {
        if(n<0)return 0;
        if(n==0)return 1;
        return countWays(n-1)+countWays(n-2)+countWays(n-3);
        // your code here
        
    }
};
```

*Generated on: 3/6/2026, 5:02:54 PM*