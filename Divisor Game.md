## 01. Divisor Game

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/divisor-game-1664432414/1?page=1&category=Dynamic%20Programming&status=solved&sortBy=submissions)

### Problem Description

**Task:** Alice and Bob take turns playing a game, with Alice starting first.Initially, there is a number n on the chalkboard. On each player's turn, that player makes a move consisting of:
Choosing any x with 0 < x < n and n % x = = 0.
Replacing the number n on the chalkboard with n - x.
Also, if a player cannot make a move, they lose the game.Return true if and only if Alice wins the game, assuming both players play optimally.
Example 1:

#### Examples

##### Example 1

- **Input:**
```text
n = 2Output: TrueExplanation: Alice chooses 1, and Bob has no more moves. Example 2:
```

##### Example 2

- **Input:**
```text
n = 3Output: FalseExplanation: Alice chooses 1, Bob chooses 1, and Alice has no more moves. Your Task:You don't need to read input or print anything. Your task is to complete the function divisorGame() which takes an integer n as a parameter and returns true if Alice wins the game. Expected Time Complexity: O(1)Expected Auxiliary Space: O(1)
```

#### Constraints

- **1.** `1 ≤ n ≤ 10³`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** Not found
- **Expected Auxiliary Space Complexity:** Not found

### Code (C++)

**Language:** `C++`

```cpp
class Solution {
  public:
    bool divisorGame(int n) {
        // code here
        return !(n&1);
    }
};
```

*Generated on: 3/6/2026, 5:07:34 PM*