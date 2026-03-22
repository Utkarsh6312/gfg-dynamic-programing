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
<<<<<<< HEAD
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
=======
Input: arr[] = [-2, 6, -3, -10, 0, 2]
Output: 180
Explanation: The subarray with maximum product is [6, -3, -10] with product = 6 * (-3) * (-10) = 180.
Input: arr[] = [-1, -3, -10, 0, 6]
Output: 30
Explanation: The subarray with maximum product is [-3, -10] with product = (-3) * (-10) = 30.
Input: arr[] = [2, 3, 4] Output: 24 Explanation: For an array with all positive elements, the result is product of all elements.
>>>>>>> 537e47abcc2e8d129880b7cc4c7b1d1527753157
```

#### Constraints

<<<<<<< HEAD
- **1.** `1 ≤ arr.size() ≤ 10⁶-10`
- **2.** `0 ≤ arr[i] ≤ 100`
=======
- 1 ≤ arr.size() ≤ 10<sup>6</sup>
- -100 ≤ arr[i] ≤ 100
>>>>>>> 537e47abcc2e8d129880b7cc4c7b1d1527753157

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Code (C++)

**Language:** `C++`

```cpp
─────────────────────────╯
   1 // This C++ code ek array mein maximum subarray product find karta hai.
   2 class Solution {
   3   public:
   4     // Yeh function ek vector 'a' mein maximum product subarray ki value return karta hai.
   5     int maxProduct(vector<int> &a) {
   6         // p: current product jo hum calculate kar rahe hain.
   7         // f: pehla negative product jo current segment mein mila hai.
   8         // b: ek flag jo batata hai ki kya humne koi zero dekha hai (1 agar dekha hai, 0 agar nahi).
   9         int p=1,f=0,b=0;
  10         // m: ab tak ka maximum product. Isko ek choti negative value se initialize kiya hai
  11         // taaki negative numbers wale cases bhi handle ho sakein.
  12         int m=-11; // Ya koi aur choti value, jaise INT_MIN.
  13
  14         // Har element ko iterate karte hain array 'a' mein.
  15         for(auto &i: a){
  16             // Agar current element zero nahi hai.
  17             if(i){
  18                 p*=i; // Current product ko update karte hain.
  19                 // Agar current product negative ho gaya hai.
  20                 if(p<0){
  21                     // Agar 'f' abhi tak set nahi hua hai (matlab yeh pehla negative product hai current segment me
  22                     if(!f)f=p;
  23                     // Agar 'f' pehle se set hai, toh iska matlab hai ki humne ek aur negative number dekha hai.
  24                     // 'p/f' karne se hum pehle negative number ko divide kar dete hain,
  25                     // jisse agar even number of negatives hain toh positive product mil jayega.
  26                     else m=max(m,(int)(p/f));
  27                 }
  28                 // Agar current product positive hai.
  29                 else m=max(m,p); // 'm' ko current product se update karte hain.
  30             }
  31             // Agar current element zero hai.
  32             else{
  33                 f=0; // 'f' ko reset karte hain kyunki zero se segment break ho jata hai.
  34                 b=1; // 'b' ko 1 set karte hain, matlab humne zero dekha hai.
  35                 p=1; // 'p' ko reset karte hain kyunki zero ke baad naya segment shuru hota hai.
  36             }
  37         }
  38         // Loop khatam hone ke baad, final 'p' ko bhi 'm' se compare karte hain.
  39         m=max(p,m);
  40         // Agar 'm' abhi bhi negative hai aur humne array mein zero dekha tha,
  41         // toh max product 0 ho sakta hai (jaise [-2, 0, -1] mein max product 0 hai).
  42         if(m<0 && b)m=0;
  43         return  m; // Maximum product return karte hain.
  44
  45     }
  46 };
```

<<<<<<< HEAD
*Generated on: 3/6/2026, 4:46:31 PM*
=======
*Generated on: 3/6/2026, 4:04:36 PM*
>>>>>>> 537e47abcc2e8d129880b7cc4c7b1d1527753157
