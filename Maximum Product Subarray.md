## 01. Maximum Product Subarray

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-product-subarray3604/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an array arr[] that contains positive and negative integers (may contain 0 as well). Find the maximum product that we can get in a subarray of arr[].

> **Note:** It is guaranteed that the answer fits in a 32-bit integer.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [-2, 6, -3, -10, 0, 2]
```
- **Output:**
```text
180
```
- **Explanation:** The subarray with maximum product is [6, -3, -10] with product = 6 * (-3) * (-10) = 180.

##### Example 2

- **Input:**
```text
arr[] = [-1, -3, -10, 0, 6]
```
- **Output:**
```text
30
```
- **Explanation:** The subarray with maximum product is [-3, -10] with product = (-3) * (-10) = 30.

##### Example 3

- **Input:**
```text
arr[] = [2, 3, 4] Output: 24 Explanation: For an array with all positive elements, the result is product of all elements.
```

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁶-10`
- **2.** `0 ≤ arr[i] ≤ 100`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int maxProduct(vector<int> &a) {
        // code here
        int p=1,f=0,b=0;
        int m=-11;
        for(auto &i: a){
            if(i){
                p*=i;
                if(p<0){
                    if(!f)f=p;
                    else m=max(m,(int)(p/f));
                }else m=max(m,p);
            }else{
                f=0;
                b=1;
                p=1;
            }
        }
        m=max(p,m);
        if(m<0 && b)m=0;
        return  m;
        
    }
};  
```

*Generated on: 3/6/2026, 4:46:31 PM*