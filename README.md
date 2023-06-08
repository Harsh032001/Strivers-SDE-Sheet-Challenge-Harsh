# Strivers-SDE-Sheet-Challenge-Harsh
                                          1- Set Matrix Zeros
Sample Input 1 :
2
2 3
7 19 3
4 21 0
3 3
1 2 3
4 0 6
7 8 9
Sample Output 1 :
7 19 0
0 0 0
1 0 3
0 0 0
7 0 9
code:

#include <bits/stdc++.h>

void setZeros(vector<vector<int>> &matrix)
{
	// Write your code here.
	int n= matrix.size();
	int m= matrix[0].size();
	int col[m] = {0};
	int row[n] = {0};
	for(int i=0; i<n ; i++){
		for(int j=0; j<m; j++){
                  if (matrix[i][j] == 0) {
                    row[i] = 1;
                    col[j] = 1;
                  
                        }
		}
	}
	for(int i=0; i<n ; i++){
		for(int j=0 ; j<m ; j++){
			if(row[i] || col[j]){
				matrix[i][j] =0;

			}
		}
	}
}
  
                                           2- pascal triangle
  #include <bits/stdc++.h>

vector<vector<long long int>> printPascal(int n) 
{
    vector<vector<long long int>> r(n);
            
            for(int i=0; i< n; i++){
                r[i].resize(i+1);
                r[i][0] = r[i][i] = 1;
                
                for(int j = 1; j<i; j++)
                    r[i][j] = r[i-1][j-1] +r[i-1][j];
            }
        return r;
}
  
                                         3-  Next Permutation
  #include <bits/stdc++.h> 
vector<int> nextPermutation(vector<int> &permutation, int n)
{
    //  Write your code here.
    int i=n-1;
    while(i>0)
    {
        if(permutation[i]>permutation[i-1])
            break;
        i--;
    }
    if(i==0)
    {
        reverse(permutation.begin(),permutation.end());
        return permutation;
    }
    i--;
    int j=n-1;
    while(j>0)
    {
        if(permutation[j]>permutation[i])
            break;
        j--;
    }
    swap(permutation[i],permutation[j]);
    reverse(permutation.begin()+i+1,permutation.end());
    return permutation ;
}
  
                                   4-  Maximum Subarray Sum
  
  #include"bits/stdc++.h"
long long maxSubarraySum(int arr[], int n)
{
   long long int sum=INT_MIN,csum=0;
   for(int i=0;i<n;i++){
       csum+=arr[i];
       if(csum<0){
           csum=0;
           }
       sum=max(sum,csum);
       }
   return sum;
}
  
                                    5-  Sort 0 1 2
  
  #include <bits/stdc++.h> 
void sort012(int *arr, int n)
{
        int lo = 0;
        int hi = n - 1;
        int mid = 0;
        
        while (mid <= hi) {
            switch (arr[mid]) {
                    // If the element is 0
                case 0:
                    swap(arr[lo++], arr[mid++]);
                    break;
                    
                    // if the element is 1
                case 1:
                    mid++;
                    break;
                    
                    // if the element is 2
                case 2:
                    swap(arr[mid], arr[hi--]);
                    break;
            }
        }
}
                        
                        
                            6-  Best time to buy and sell stock
                        
#include <bits/stdc++.h> 
int maximumProfit(vector<int> &prices){
    int maxPro = 0;
        int minPrice = INT_MAX;
        for(int i = 0; i < prices.size(); i++){
            minPrice = min(minPrice, prices[i]);
            maxPro = max(maxPro, prices[i] - minPrice);
            
        }
        return maxPro;
    }

                               7-  Rotate image
   class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        for(int i=0 ; i<n ; i++)
            for(int j=0 ; j<i ; j++)
        swap(matrix[i][j] , matrix[j][i]);
        for(int i=0 ; i<n ; i++)
        reverse(matrix[i].begin(), matrix[i].end());
    }
};
                          
                            8-   Merged Overlapping interval
                          
vector<vector<int>> mergeIntervals(vector<vector<int>> &intervals)
{
     int n = intervals.size();
     sort(intervals.begin(), intervals.end());
    if (n <= 1) {
        return intervals;
    }
    vector<vector<int>> ans;
    ans.push_back(intervals[0]);
 
    for (int i = 1; i < n; i++) {
        if (intervals[i][0] <= ans.back()[1]) {
            ans.back()[1] = max(ans.back()[1], intervals[i][1]);
        } else {

            ans.push_back(intervals[i]);
        }
    } 
    return ans;
}
                                 
                                9- Merged two sorted arrays without extra space
  #include <bits/stdc++.h>

vector<int> ninjaAndSortedArrays(vector<int>& arr1, vector<int>& arr2, int m, int n) {
	vector<int> merged;
   for(int i=0; i<arr1.size();i++){
        if(arr1[i]==0){
            continue;
        }
       merged.push_back(arr1[i]);
   }

    for(int i=0; i<arr2.size();i++){
        if(arr2[i]==0){
            continue;
        }
       merged.push_back(arr2[i]);
   }

   sort(merged.begin(), merged.end());
   return merged;
}
  
 //leetcode
  class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int p1 = m-1, p2 = n -1, i= m+n-1;
     while(p2 >= 0){
        if(p1 >= 0&& nums1[p1] >nums2[p2]){
        nums1[i--]= nums1[p1--];                                                               
          }
        else{
        nums1[i--]= nums2[p2--];
      }
     }
        
    }
};
  
                               10- find the duplicate in an array of N+1 integers
  #include <bits/stdc++.h>

int findDuplicate(vector<int> &arr, int n){
	int fast = arr[0];
	int slow = arr[0];
	do{
		slow = arr[slow];
		fast = arr[arr[fast]];
		
	}while(slow != fast);
	fast= arr[0];
	while(fast != slow){
		fast = arr[fast];
		slow = arr[slow];
	}
	return slow;
}
                                 11- Repeat and missing numbers
  
  #include <bits/stdc++.h>

pair<int,int> missingAndRepeating(vector<int> &arr, int n)
{
		// Write your code here 
unordered_map<int,int>tally;
   for(int i=0;i<n;i++){
       tally[arr[i]]++;
   }
   pair<int,int>ans;
   for(int i=1;i<=arr.size();i++){
       if(tally[i]>1){
           ans.second=i;
       }
       if(tally[i]==0){
           ans.first=i;
       }
   }
   return ans;
}
	
                              13 Search in a 2D matrix
  bool searchMatrix(vector<vector<int>>& mat, int target) {
   if(!mat.size()){ 
            return false;
        }
        
        int n = mat.size();
        int m = mat[0].size();
        
        int lo = 0;
        int hi = (n*m) - 1;
        
        while(lo <= hi){
            int mid = (lo + (hi - lo)/2);
            if(mat[mid/m][mid%m] == target){
                return true;
            }
            if(mat[mid/m][mid % m] < target) {
                lo = mid + 1;
            }
            else {
                hi = mid - 1;
            }
        }
        return false;
    }


                          
                          
                                 23-  count subarray with given XOR

 #include <bits/stdc++.h>

int subarraysXor(vector<int> &arr, int x)
{
    int xr= 0;
        unordered_map<int,int> mpp;
        mpp[xr]++;
        int cnt =0;
        for(int i=0 ; i<arr.size(); i++){
            xr = xr ^ arr[i] ;
            int y= xr ^ x;
            cnt += mpp[y];
            mpp[xr]++;
        }
          return cnt;
}
