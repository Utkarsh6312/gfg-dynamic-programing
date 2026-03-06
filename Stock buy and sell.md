## 01. Stock buy and sell

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/stock-buy-and-sell-1587115621/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Given an array arr[] denoting the cost of stock on each day, the task is to find the maximum total profit if we can buy and sell the stocks any number of times.

> **Note:** We can only sell a stock which we have bought earlier and we cannot hold multiple stocks on any day.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [100, 180, 260, 310, 40, 535, 695]
```
- **Output:**
```text
865
```
- **Explanation:** Buy the stock on day 0 and sell it on day 3 = > 310 – 100 = 210 Buy the stock on day 4 and sell it on day 6 = > 695 – 40 = 655 Maximum Profit = 210 + 655 = 865

##### Example 2

- **Input:**
```text
arr[] = [4, 2, 2, 2, 4]
```
- **Output:**
```text
2
```
- **Explanation:** Buy the stock on day 3 and sell it on day 4 = > 4 – 2 = 2

##### Example 3

- **Input:**
```text
arr[] = [4, 2]
```
- **Output:**
```text
0
```
- **Explanation:** Don't Buy the stock.

#### Constraints

- **1.** `2 ≤ arr.size() ≤ 10⁶`
- **2.** `0 ≤ arr[i] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    int stockBuySell(vector<int> &a) {
        // code here
        int c=0,s=0,n=a.size();bool b=0;
        for(int i=1;i<n;i++){
            // cout<<c<<" "<<s<<"\n";
            if(b){
                if(i==n-1 && a[i]>a[i-1]){
                    s+=a[i]-c;                    
                }
                else if(a[i]>a[i-1])continue;
                else {
                    s+=(a[i-1]-c);
                    c=a[i];
                }
            }else{
                if(i==n-1 && a[i]>a[i-1]){
                    s=a[i]-a[i-1];                    
                }else if(a[i]>a[i-1]){
                    c=a[i-1];b=1;
                }
                else continue;
            }
        }return s;
    }
};
```

*Generated on: 3/6/2026, 5:01:52 PM*