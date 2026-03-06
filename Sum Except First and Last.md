## 01. Sum Except First and Last

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/max-length-chain/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** You are given an array arr of numbers. Return the sum of all the elements except the first and last elements.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [5, 24, 39, 60, 15, 28, 27, 40, 50, 90]
```
- **Output:**
```text
283
```
- **Explanation:** The sum of all the elements except the first and last element is 283.

##### Example 2

- **Input:**
```text
arr[] = [5, 10, 1, 11]
```
- **Output:**
```text
11
```
- **Explanation:** The sum of all the elements except the first and last element is 11.

##### Example 3

- **Input:**
```text
arr[] = [5, 10]
```
- **Output:**
```text
0
```
- **Explanation:** The sum of all the elements except the first and last element is 0.

#### Constraints

- **1.** `2 <= arr.size() <= 10⁵`
- **2.** `2 <= arr[i] <= 10⁵^`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    /*You are required to complete this method*/
    int rec(vector<int>& a,int i, int n){
        if(i>=n-1)return 0;
        return a[i]+rec(a,i+1,n);
    }
    int sumExceptFirstLast(vector<int>& a) {
        // Your code here
        return rec(a,1,a.size());
    }
};
```

*Generated on: 3/6/2026, 5:03:11 PM*