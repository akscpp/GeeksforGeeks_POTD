[Problem Link](https://www.geeksforgeeks.org/problems/search-in-a-rotated-array4618/1)<br>

Given a sorted (in ascending order) and rotated array arr of distinct elements which may be rotated at some point and given an element key, the task is to find the index of the given element key in the array arr. The whole array arr is given as the range to search.<br>

Rotation shifts elements of the array by a certain number of positions, with elements that fall off one end reappearing at the other end.<br>

Note:- 0-based indexing is followed & returns -1 if the key is not present.<br>

Examples :<br>

Input: arr[] = [5, 6, 7, 8, 9, 10, 1, 2, 3], key = 10<br>
Output: 5<br>
Explanation: 10 is found at index 5.<br>
Input: arr[] = [3, 5, 1, 2], key = 6<br>
Output: -1<br>
Explanation: There is no element that has value 6.<br>
Expected Time Complexity: O(log n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 ≤ arr.size() ≤ 10^6<br>
0 ≤ arr[i] ≤ 10^6<br>
1 ≤ key ≤ 10<br>

__Intuition ->Use Binary Search. If key is present at mid , return mid. If not , then find the sorted half and search in that half.__

```C++
int search(vector<int>& arr, int key) {
        int low = 0;
        int high = arr.size()-1;
        
        while(low<=high){
            int mid = low+(high-low)/2;
            
            if(arr[mid]==key) return mid;
            
            if(arr[mid]>=arr[low]){
                if(key>=arr[low] && key<=arr[mid]){
                    high = mid-1;
                }else{
                    low=mid+1;
                }
            }
            
            if(arr[mid]<=arr[high]){
                if(key>=arr[mid] && key<=arr[high]){
                    low=mid+1;
                }else{
                    high = mid-1;
                }
            }
        }
        
        return -1;
    }
```
