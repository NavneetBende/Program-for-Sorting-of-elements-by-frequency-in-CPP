Sorting of elements by frequency in C++
Here, in this page we will discuss the program for sorting of elements by frequency frequency in C++ programming language. We are given with an integer array and need to sort the array on the basis of there occurence.

Sorting element in array by frequency using C++
Sort Elements by Frequency of Occurrences in C++
To solve sort elements by frequency of occurrences in C we can use an array to count the occurrences of each element , and then use a sorting algorithm to sort the elements by their counts . Lets see this in detail .

Sort elements by frequency of occurrences code in C
Method Discussed :
Method 1 : Naive Approach
Method 2 : Using Hash-map and then sorting.
Let’s discuss both methods one by one in brief.
Method 1 :
First we declare an array.
Declare two 2d array arr[MAX][2] and brr[MAX][2].
Store 1d array in 0th index of arr array.
Set arr[][1] = 0for all indexes upto n.
Now, count the frequency of elements of the array.
If element is unique the push it at brr[][0] array, and its frequency will represent by brr[][1].
Now, sort the brr on the basis of frequency.
Print the brr array on basis of their frequency.
Method 1 :
Run
#include <bits/stdc++.h>
using namespace std;
#define MAX 256
int main ()
{
     int a[]={10, 20, 10, 10, 20, 30, 30, 30, 30, 0};
     int n = sizeof(a)/sizeof(a[0]);
     int arr[MAX][2], brr[MAX][2];
     int k = 0, temp, count;
     
     for (int i = 0; i < n; i++){
          arr[i][0] = a[i];
          arr[i][1] = 0;
     }
     
     // Unique elements and its frequency are stored in another array
     for (int i = 0; i < n; i++){
         if (arr[i][1])
            continue;
         count = 1;
         for (int j = i + 1; j < n; j++){
            if (arr[i][0] == arr[j][0]){
               arr[j][1] = 1;
               count++;
            }
         }
         brr[k][0] = arr[i][0];
         brr[k][1] = count;
         k++;
    }
    n = k;

    //Store the array and its frequency in sorted form
    for (int i = 0; i < n - 1; i++)
    {
        temp = brr[i][1];
        for (int j = i + 1; j < n; j++)
        {
           if (temp < brr[j][1])
           {
                 temp = brr[j][1];
                 brr[j][1] = brr[i][1];
                 brr[i][1] = temp;

                 temp = brr[j][0];
                 brr[j][0] = brr[i][0];
                 brr[i][0] = temp;
            }
        }
    }
    for (int i = 0; i < n; i++)
    {
        while (brr[i][1] != 0)
        {
           cout<< brr[i][0] <<" ";
           brr[i][1]--;
        }
    }
    return 0;
}
Output
30 30 30 30 10 10 10 20 20 0
