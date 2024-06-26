Minimum number of Jumps to reach the end of an array in C++
Here, in this page we will discuss the program to find Minimum number of Jumps to reach the end of an array in C++ . We are Given with an array of integers where each element represents the max number of steps that can be made forward from that element. We need to Write a code to return the minimum number of jumps to reach the end of the array (starting from the first element). If an element is 0, they cannot move through that element. If the end isn’t reachable, return -1.

Minimum number of Jumps to reach the end of an array in C++
Algorithm :
Take the size of the array from the user and store it in variable say n.
Take n elements of the array from the user.
Create another function say minJumps() that will return the desired output.
Inside that minJumps(), Make a jumps[] array from left to right such that jumps[i] indicate the minimum number of jumps needed to reach arr[i] from arr[0].
To fill the jumps array run a nested loop inner loop counter is j and outer loop count is i.
Outer loop from 1 to n-1 and inner loop from 0 to i.
if i is less than j + arr[j] then set jumps[i] to minimum of jumps[i] and jumps[j] + 1. initially set jump[i] to INT MAX
Finally, return jumps[n-1].
Minimum number of jumps in C++
Code in C++
#include <bits/stdc++.h>
using namespace std;

int minJumps(int arr[], int n)
{
  // jumps[n-1] will hold the result
  int jumps[n];
  int i, j;

  if (n == 0 || arr[0] == 0)
    return INT_MAX;

  jumps[0] = 0;

  // Find the minimum number of jumps to reach arr[i]
  // from arr[0], and assign this value to jumps[i]
  for (i = 1; i < n; i++) {
    jumps[i] = INT_MAX;
    for (j = 0; j < i; j++) {
      if (i <= j + arr[j] && jumps[j] != INT_MAX)  
           { 
               jumps[i] = min(jumps[i], jumps[j] + 1); 
               break; 
           } 
        } 
    } 
   return jumps[n - 1]; 
 } 
int main() 
{ 
   int n; 
   cin>>n;
   int arr[n];

   for(int i=0; i<n; i++) cin>>arr[i];

   cout<<"Minimum number of jumps to reach end is "<< minJumps(arr, n);

   return 0;
}
Output
Input :

6

1 3 6 1 0 9

Output :

Minimum number of jumps to reach end is 3
