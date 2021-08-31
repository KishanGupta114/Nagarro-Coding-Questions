# Nagarro-Coding-Questions

### These questions are asked by Nagarro's Coding Rounds. And there will be 3 questions to be solved in 90 minutes.

```
Q1. Find Number of Selective Arrangements...
```

```cpp
// A Naive Recursive C++ program
// to count derangements
#include <iostream>
using namespace std;

//By Recursion
// int solve(int n){
//   if(n == 1) return 0;  // Base Case -- Cause: if we take n = {0} then possibilities = 0
//   if(n == 2) return 1;  // Base Case -- Cause: if we take n = {0, 1} then possibilities = 1
  
//   return (n-1) * (solve(n-1) + solve(n-2));
// }
int main() 
{
    // int n;
    // cin>>n;
    // cout <<solve(n);
    
    
    // By Dynamic Programming.. [Where:: Time Complexity == O(n) & Space Complexity == O(n)]
    // int n;
    // cin>>n;
    // int dp[n + 1] = {0};
    // dp[1]=0;
    // dp[2]=1;
    // for(int i=3;i<=n;++i)
    //   dp[i]=(i-1)*(dp[i-1]+dp[i-2]);
      
    // cout<<dp[n];
    
    
    
    // By Dynamic Programming But Optimized Solution.. [Where:: Time Complexity == O(n) & Space Complexity == O(1)]
    int n;
    cin>>n;
    int dp[n + 1] = {0};
    
    int a = 0; //dp[1] replaced by a;
    int b = 1; //dp[2] replaced by b;
    
    for(int i=3;i<=n;++i){
      int temp = (i-1) * (b+a);
      a = b;
      b = temp;
    }
    
    cout<<b;
    
    return 0;
}

```

```
Q2. Find HCF of N Elements....
```

```cpp
// C++ program to find GCD of two or
// more numbers
#include <bits/stdc++.h>
using namespace std;

// Function to return gcd of a and b
int gcd(int a, int b)
{
	if (a == 0)
		return b;
	return gcd(b % a, a);
}

// Function to find gcd of array of
// numbers
int findGCD(int arr[], int n)
{
	int result = arr[0];
	for (int i = 1; i < n; i++)
	{
		result = gcd(arr[i], result);

		if(result == 1)
		{
		return 1;
		}
	}
	return result;
}

// Driver code
int main()
{
	int arr[] = { 2, 4, 6, 8, 16 };
	int n = sizeof(arr) / sizeof(arr[0]);
	cout << findGCD(arr, n) << endl;
	return 0;
}

```

```
Q3. Find Maximum Cccurring Character in Input String.....
```

```cpp
// C++ implementation to find
// the maximum occurring character in
// an input string which is lexicographically first
#include <bits/stdc++.h>
using namespace std;

// function to find the maximum occurring character in
// an input string which is lexicographically first
char getMaxOccurringChar(char str[])
{
	// freq[] used as hash table
	int freq[26] = { 0 };

	// to store maximum frequency
	int max = -1;

	// to store the maximum occurring character
	char result;

	// length of 'str'
	int len = strlen(str);

	// get frequency of each character of 'str'
	for (int i = 0; i < len; i++)
		freq[str[i] - 'a']++;

	// for each character, where character is obtained by
	// (i + 'a') check whether it is the maximum character
	// so far and accodingly update 'result'
	for (int i = 0; i < 26; i++)
		if (max < freq[i]) {
			max = freq[i];
			result = (char)(i + 'a');
		}

	// maximum occurring character
	return result;
}

// Driver Code
int main()
{
	char str[] = "sample program";
	cout << "Maximum occurring character = "
		<< getMaxOccurringChar(str);
	return 0;
}

```
