[Problem Link](https://www.geeksforgeeks.org/problems/count-pairs-in-an-array4145/1)<br>
Given an array arr of n integers, count all pairs (arr[i], arr[j]) in it such that i*arr[i] > j*arr[j] and 0 ≤ i < j < n.<br>

Note: 0-based Indexing is followed.<br>

Example 1:<br>

Input :<br>
n = 4<br>
arr[] = {8, 4, 2, 1}<br>
Output :<br>
2<br>
Explanation:<br>
If we see the array after operations<br>
[0*8, 1*4, 2*2, 3*1] => [0, 4, 4, 3]<br>
Pairs which hold the condition i*arr[i] > j*arr[j] are (4,1) and (2,1), so in total 2 pairs are available.<br>
Example 2:<br>

Input :
n = 7<br>
arr[] = {5, 0, 10, 2, 4, 1, 6}<br>
Output:<br>
5<br>
Explanation :<br>
Pairs which hold the condition i*arr[i] > j*arr[j] are (10,2), (10,4), (10,1), (2,1) and (4,1), so in total 5 pairs are there.<br>
Your Task:  <br>
You don't need to read input or print anything. Your task is to complete the function countPairs() which takes the array arr[] and its size n as inputs and returns the required result.<br>

Expected Time Complexity: O(n*log(n))<br>
Expected Auxiliary Space: O(n*log(n))<br>

Constraints:<br>
1 ≤ n ≤ 10^4<br>
0 ≤ arr[i] ≤ 10^4<br>

__Intuition -> Modify the array so that arr[i] becomes arr[i]*i. Then use count Inversion in an array.__

```C++
int merge(vector<int> &arr, int low, int mid, int high) {
    vector<int> temp; 
    int left = low;      
    int right = mid + 1;  

    
    int cnt = 0;

    

    while (left <= mid && right <= high) {
        if (arr[left] <= arr[right]) {
            temp.push_back(arr[left]);
            left++;
        }
        else {
            temp.push_back(arr[right]);
            cnt += (mid - left + 1); 
            right++;
        }
    }

    

    while (left <= mid) {
        temp.push_back(arr[left]);
        left++;
    }

    
    while (right <= high) {
        temp.push_back(arr[right]);
        right++;
    }

    
    for (int i = low; i <= high; i++) {
        arr[i] = temp[i - low];
    }

    return cnt; 
}

int mergeSort(vector<int> &arr, int low, int high) {
    int cnt = 0;
    if (low >= high) return cnt;
    int mid = (low + high) / 2 ;
    cnt += mergeSort(arr, low, mid);  
    cnt += mergeSort(arr, mid + 1, high); 
    cnt += merge(arr, low, mid, high); 
    return cnt;
}
    int countPairs(int arr[] , int n ) 
    {
        // Your code goes here 
        vector<int>ans(n,0);
        for(int i=0;i<n;i++){
            
            ans[i]=arr[i]*i;
        }
        
        return mergeSort(ans,0,n-1);
    }
```
