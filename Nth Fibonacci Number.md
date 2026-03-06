## 01. Nth Fibonacci Number |

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/nth-fibonacci-number1335/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

Given a non-negative integer n, your task is to find the nth Fibonacci number.
The Fibonacci sequence is a sequence where the next term is the sum of the previous two terms. The first two terms of the Fibonacci sequence are 0 followed by 1. The Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21
The Fibonacci sequence is defined as follows:
```
F(0) = 0
F(1) = 1
F(n) = F(n - 1) + F(n - 2) for n > 1
```

#### Examples

```
Input: n = 5
```

```
Output: 5
```

Explanation: The 5th Fibonacci number is 5.
```
Input: n = 0
```

```
Output: 0
```

Explanation: The 0th Fibonacci number is 0.
```
Input: n = 1
```

```
Output: 1
```

Explanation: The 1st Fibonacci number is 1.
```
Constraints:0 ≤ n ≤ 30
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)Auxiliary Space: O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (Code)

```
// User function Template for C++
class Solution {
  public:
    int rec(int n,int f,int s,int c){
        if(n==0)return 0;
        if(n==1)return 1;
        if(n==c)return f+s;
        return rec(n,s,f+s,c+1);
    }
    int nthFibonacci(int n) {
        // code here
        return rec(n,0,1,2);
    }
};
```

*Generated on: 3/6/2026, 3:28:12 PM*