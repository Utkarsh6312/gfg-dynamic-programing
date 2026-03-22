## 01. Perfect Sum Problem

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1?page=1&category=Dynamic%20Programming&sortBy=submissions)

### Problem Description

**Task:** Given an array arr of non-negative integers and an integer target, the task is to count all subsets of the array whose sum is equal to the given target.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [5, 2, 3, 10, 6, 8], target = 10
```
- **Output:**
```text
3
```
- **Explanation:** The subsets {5, 2, 3}, {2, 8}, and {10} sum up to the target 10.

##### Example 2

- **Input:**
```text
arr[] = [2, 5, 1, 4, 3], target = 10
```
- **Output:**
```text
3
```
- **Explanation:** The subsets {2, 1, 4, 3}, {5, 1, 4}, and {2, 5, 3} sum up to the target 10.

##### Example 3

- **Input:**
```text
arr[] = [5, 7, 8], target = 3Output: 0
```
- **Explanation:** There are no subsets of the array that sum up to the target 3.

##### Example 4

- **Input:**
```text
arr[] = [35, 2, 8, 22], target = 0Output: 1
```
- **Explanation:** The empty subset is the only subset with a sum of 0.

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10³⁰ ≤ arr[i] ≤ 10³⁰ ≤ target ≤ 10³`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n*target)
- **Expected Auxiliary Space Complexity:** O(n*target)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-03-22 12:48:35
- **Status:** Correct
- **Marks:** 0

```cpp
// Yeh file ek solution provide karta hai jisme hum ek array ke subsets ka count find karte hain jinka sum ek given target ke barabar ho.
class Solution {
  public:
    // Yeh function count karta hai ki kitne subsets ka sum 'target' ke barabar hai.
    // 'arr': Input array jisme numbers hain.
    // 'target': Woh sum jo humein subsets mein chahiye.
    int perfectSum(vector<int>& arr, int target) {
        int n = arr.size(); // 'n' array mein elements ka total count hai.
        const int MOD = 1e9 + 7; // Bade answers ko handle karne ke liye hum MOD ka use karte hain, taaki integer overflow na ho.
        
        // 'dp' array banate hain. dp[i] store karega ki 'i' sum banane ke kitne tarike hain.
        // Iska size (target + 1) hai kyunki humein sum 0 se lekar target tak ke liye counts chahiye.
        vector<int> dp(target + 1, 0);
        dp[0] = 1;  // Base case: Sum 0 banane ka ek hi tarika hai - empty subset (koi element na lo).
        
        // Har ek number ko 'arr' mein iterate karte hain.
        for (int i = 0; i < n; i++) {
            // Ab hum har possible sum ko 'target' se lekar 0 tak iterate karte hain.
            // Hum backwards (ulta) iterate karte hain taaki ek hi number ko ek hi iteration mein baar-baar use na karein.
            // Matlab, agar humne arr[i] ko current sum mein include kiya hai, toh woh arr[i] is iteration mein dobara use na ho.
            for (int sum = target; sum >= 0; sum--) {
                // Agar current number (arr[i]) ko 'sum' mein se minus karne ke baad bhi sum non-negative rehta hai,
                // toh matlab hum arr[i] ko current 'sum' banane ke liye use kar sakte hain.
                if (sum - arr[i] >= 0) {
                    // dp[sum] ko update karte hain.
                    // dp[sum] = (purane tarike 'sum' banane ke) + (nayi tarike 'sum' banane ke, jisme hum arr[i] ko include karte hain).
                    // Naye tarike: Agar hum arr[i] ko include karte hain, toh baaki sum (sum - arr[i]) banane ke jitne tarike the,
                    // woh sab ab 'sum' banane ke tarike ban jayenge jab hum arr[i] ko add karenge.
                    dp[sum] = (dp[sum] + dp[sum - arr[i]]) % MOD;
                }
            }
        }
        
        // Finally, dp[target] mein woh count hoga ki kitne subsets ka sum 'target' ke barabar hai.
        return dp[target];
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-03-21 20:50:35
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int perfectSum(vector<int>& arr, int target) {
        int n = arr.size();
        const int MOD = 1e9 + 7;
        
        vector<int> dp(target + 1, 0);
        dp[0] = 1;  // empty subset
        
        for (int i = 0; i < n; i++) {
            for (int sum = target; sum >= 0; sum--) {
                if (sum - arr[i] >= 0) {
                    dp[sum] = (dp[sum] + dp[sum - arr[i]]) % MOD;
                }
            }
        }
        
        return dp[target];
    }
};
```

*Generated on: 3/22/2026, 12:50:33 PM*