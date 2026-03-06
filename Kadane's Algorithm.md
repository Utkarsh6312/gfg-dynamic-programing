## 01. Kadane's Algorithm |

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

You are given an integer array arr[]. You need to find the maximum sum of a subarray (containing at least one element) in the array arr[].
Note : A subarray is a continuous part of an array.
#### Examples

```
Input: arr[] = [2, 3, -8, 7, -1, 2, 3]
```

```
Output: 11
```

```
Explanation: The subarray [7, -1, 2, 3] has the largest sum 11.
```

```
Input: arr[] = [-2, -4]
```

```
Output: -2
```

```
Explanation: The subarray [-2] has the largest sum -2.
```

```
Input: arr[] = [5, 4, 1, 7, 8]
```

```
Output: 25
```

```
Explanation: The subarray [5, 4, 1, 7, 8] has the largest sum 25.
```

```
Constraints:1 ≤ arr.size() ≤ 10^5-10^4 ≤ arr[i] ≤ 10^4
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)Auxiliary Space: O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (Code)

```
class Solution {
  public:
    int maxSubarraySum(vector<int> &a) {
        // Code here
        int  n=a.size();
        int s=a[0],m=a[0];
        for(int i=1;i<n;i++){
            int x=a[i];
            s=max(a[i],a[i]+s);
            m=max(m,s);
        }
        return m;
    }
};
```

*Generated on: 3/6/2026, 3:28:53 PM*