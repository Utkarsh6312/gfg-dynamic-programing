## 01. Maximum Sum Bitonic Subsequence

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-sum-bitonic-subsequence1857/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an array arr[] of n integers. A subsequence of arr[] is called Bitonic if it first increases and then decreases. Find the max sum bitonic subsequence.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [1, 15, 51, 45, 33, 100, 12, 18, 9]
```
- **Output:**
```text
194
```
- **Explanation:** Bi-tonic Sub-sequence are : {1, 51, 9} or {1, 51, 100, 18, 9} or {1, 15, 51, 100, 18, 9} or {1, 15, 45, 100, 12, 9} or {1, 15, 45, 100, 18, 9} .. so on Maximum sum Bi-tonic sub-sequence is 1 + 15 + 51 + 100 + 18 + 9 = 194

##### Example 2

- **Input:**
```text
arr[] = [80, 60, 30, 40, 20, 10]
```
- **Output:**
```text
210
```
- **Explanation:** Here the sequence is strinctly decreasing. Expected Time Complexity: O(n^2)Expected Auxiliary Space: O(n)

#### Constraints

- **1.** `1 <= arr.size() <= 10³`
- **2.** `1 <= arr[i] <= 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** Not found
- **Expected Auxiliary Space Complexity:** Not found

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int maxSumBS(vector<int>& arr) {
        // code here
        int n = arr.size();
        vector<long long> inc(n),dec(n);
        // pahle inc dp array fill karenge
        for(int i=0;i<n;i++){
            inc[i] = arr[i];
            for(int j=0;j<i;j++){
                if(arr[i]>arr[j]){
                    inc[i]=max(inc[i],arr[i]+inc[j]);
                }
            }
        }
        // secondly dec dp array fill karenge
        for(int i=n-1;i>=0;i--){
            dec[i] = arr[i];
            for(int j=n-1;j>i;j--){
                if(arr[i]>arr[j]){
                    dec[i]=max(dec[i],arr[i]+dec[j]);
                }
            }
        }
        // ab inc aur dec array ke corresponding index ka sum nikalenge aur max sum ko return karenge
        long long ans = 0;
        for(int i=0;i<n;i++){
            ans = max(ans,inc[i]+dec[i]-arr[i]);
        }
        // -arr[i] isliye kiya kyuki inc aur dec array dono me arr[i] add ho raha hai to usko ek baar minus karna padega
        return (int)ans;
    }
};
```

*Generated on: 3/6/2026, 5:08:29 PM*