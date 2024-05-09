[Problem Link](https://www.geeksforgeeks.org/problems/divisor-game-1664432414/1)<br>
Alice and Bob take turns playing a game, with Alice starting first.<br>
Initially, there is a number n on the chalkboard. On each player's turn, that player makes a move consisting of:<br>

Choosing any x with 0 < x < n  and n % x == 0.<br>
Replacing the number n on the chalkboard with n - x.<br>
Also, if a player cannot make a move, they lose the game.<br>
Return true if and only if Alice wins the game, assuming both players play optimally.<br>

 

Example 1:<br>

Input:
n = 2<br>
Output: True<br>
Explanation: Alice chooses 1, and Bob has no more moves.<br>
 

Example 2:<br>

Input:
n = 3<br>
Output: False<br>
Explanation: Alice chooses 1, Bob chooses 1, and Alice has no more moves.<br>
 

Your Task:
You don't need to read input or print anything. Your task is to complete the function divisorGame() which takes an integer n as a parameter and returns true if Alice wins the game.<br>

Expected Time Complexity: O(1)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
1 ≤ n ≤ 10^3<br>

__Intuition ->If n is even , n-1 will give odd which will gave chance to Alice. If n is odd , n-1 will give even , which will not give Alice a chance.__

```C++
bool divisorGame(int n) {
        // code here
        return (n%2==0)?true:false;
    }
```
