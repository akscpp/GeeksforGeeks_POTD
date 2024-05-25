[Problem Link](https://www.geeksforgeeks.org/problems/you-and-your-books/1)<br>
You have n stacks of books. Each stack of books has some nonzero height arr[i] equal to the number of books on that stack ( considering all the books are identical and each book has a height of 1 unit ). In one move, you can select any number of consecutive stacks of books such that the height of each selected stack of books arr[i] <= k. Once such a sequence of stacks is chosen, You can collect any number of books from the chosen sequence of stacks.
What is the maximum number of books that you can collect this way?<br>

Example 1<br>

Input<br>
8 1<br>
3 2 2 3 1 1 1 3<br>
Output<br>
3<br>
Explanation <br>
We can collect maximum books from consecutive stacks numbered 5, 6, and 7 having height less than equal to K.<br>
Example 2<br>

Input<br>
8 2<br>
3 2 2 3 1 1 1 3<br>
Output<br>
4<br>
Explanation<br>
We can collect maximum books from consecutive stacks numbered 2 and 3 having height less than equal to K.<br>
Your Task:<br>
You don't have to read input or print anything. Your task is to complete the function max_Books() which takes the integer arr, n, and k returns the maximum number of books you can collect.<br>

Expected Time Complexity: O(n)<br>
Expected Space Complexity: O(1)<br>

Constraints:<br>
1 <= n <= 10^5<br>
1 <= k <= 10^9<br>
1 <= arr[i] <= 10^9<br>

__Intuition->Iterate over the array and check if the current element is less than or equal to k or not . If it is <= k , then include it in sum and choose maximum. When an element > k is encountered , set the current sum to 0.__

```C++
long long max_Books(int arr[], int n, int k) {
        // Your code here
        long long sum = 0;
        long long res = 0;
        
        for(int i=0;i<n;i++){
            if(arr[i]<=k){
                sum+=arr[i];
                res = max(res,sum);
            }else{
                sum=0;
            }
        }
        return res;
            
    }
```
