---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# Matrix Chain Multiplication
Given the dimension of a sequence of matrices in an array arr[], where the dimension of the ith matrix is (arr[i-1] * arr[i]), the task is to find the most efficient
way to multiply these matrices together such that the total number of element multiplications is minimum. When two matrices of size m*n and n*p when multiplied, 
they generate a matrix of size m*p and the number of multiplications performed is m*n*p.

### Examples:

Input: arr[] = [2, 1, 3, 4]
Output: 20
Explanation: There are 3 matrices of dimensions 2×1, 1×3, and 3×4, 
Let the input 3 matrices be M1, M2, and M3. There are two ways to multiply ((M1 x M2) x M3) and (M1 x (M2 x M3)), 
Please note that the result of M1 x M2 is a 2 x 3 matrix and result of (M2 x M3) is a 1 x 4 matrix.
((M1 x M2) x M3)  requires (2 x 1 x 3)  +  (2 x 3 x 4) = 30 
(M1 x (M2 x M3))  requires (1 x 3 x 4) +  (2 x 1 x 4) = 20 
The minimum of these two is 20.

Input: arr[] = [1, 2, 3, 4, 3]
Output: 30
Explanation: There are 4 matrices of dimensions 1×2, 2×3, 3×4, 4×3. Let the input 4 matrices be M1, M2, M3 and M4. The minimum number of multiplications are obtained
by ((M1M2)M3)M4. The minimum number is 1*2*3 + 1*3*4 + 1*4*3 = 30

Input: arr[] = [3, 4]
Output: 0
Explanation: As there is only one matrix so, there is no cost of multiplication.

### Table of Content

- [Naive Approach ] Using Recursion – O(2^n) and O(n) Space
- [Better Approach 1 ] Using Top-Down DP (Memoization) – O(n*n*n) and O(n*n) Space
- [Better Approach 2 ] Using Bottom-Up DP (Tabulation) – O(n*n*n) and O(n*n) Space
- [Naive Approach ] Using Recursion – O(2^n) and O(n) Space
We can solve the problem using recursion based on the following facts and observations:

Now, for a given chain of n matrices, the first partition can be done in n-1 ways. For example, sequence of matrices M1, M2, M3 and M4 can be grouped as
(M1)(M2 x M3 x M4), (M1x M2) x (M3 x M4) or ((M1 x M2 x M3) x M4) in these 3 ways. 

For n matrices M1, M2, ….. Mn. we can put the first bracket n-1 ways

(M1) x (M2 x M3 x M4 ……… Mn-1 x Mn)
(M1 x M2) x (M3 x M4………. Mn-1 x Mn)
(M1 x M2 x M3) x (M4 ………. Mn-1 x Mn)
……………………………………………………………………
……………………………………………………………………
(M1 x M2 x M3 x M4 ……….Mn-1) x (Mn)
We put the first bracket at different n-1 places and then recursively call for the two parts. At the end, we return the minimum of all partitions.

To write a recursive function we use a range of indexes [i, j].  And run a loop for k = i + 1 to j.  For k = i + 1, we put the first bracket after the
first matrix which has dimensions arr[i] x arr[i+1] and before the remaining matrices which have dimensions
arr[i+1] x arr[i+2],  arr[i+2] x arr[i+3], ……….. arr[j-1] x arr[j]    

- For every k, we make two subproblems : (a) Chain from i to k  (b) Chain from k to j
- Each of the subproblems can be further partitioned into smaller subproblems and we can find the total required multiplications by solving for each of the groups.
- The base case would be when we have only one matrix left which means when j is equal to i+1
 ### [Better Approach 1 ] Using Top-Down DP (Memoization) – O(n*n*n) and O(n*n) Space
Let’s suppose we have four matrices (M1, M2, M3, M4). Based on the recursive approach described above, we can construct a recursion tree.
However, we can observe that some problems are computed multiple times. To avoid this redundant computation, we can implement memoization to store the results
of previously computed inputs.
![image](https://github.com/user-attachments/assets/f1a5917e-f629-4b4f-bae7-2902ce6a1f29)
If observed carefully you can find the following two properties:
### (1) Optimal Substructure:
  In the above case, we are breaking the bigger groups into smaller subgroups and solving them to finally find the minimum number of multiplications.
  Therefore, it can be said that the problem has optimal substructure property.
### (2) Overlapping Subproblems:
    We can see in the recursion tree that the same subproblems are called again and again and this problem has the Overlapping Subproblems property. 
So Matrix Chain Multiplication problem has both properties of a dynamic programming problem. So recomputations of same subproblems can be avoided by constructing  
a temporary array memo[][] in a bottom up manner.
Follow the below steps to solve the problem:
- Build a matrix memo[][] of size n*n for memoization purposes.
- Use the same recursive call as done in the above approach:
   --When we find a range (i, j) for which the value is already calculated, return the minimum value for that range (i.e., memo[i][j]).
   --Otherwise, perform the recursive calls as mentioned earlier.
-The value stored at memo[0][n-1] is the required answer.
### [Better Approach 2 ] Using Bottom-Up DP (Tabulation) – O(n*n*n) and O(n*n) Space
In iterative approach, we initially need to find the number of multiplications required to multiply two adjacent matrices. We can use these values to find the
minimum multiplication required for matrices in a range of length 3 and further use those values for ranges with higher length. 
The iterative implementation is going to be tricky here we initially know diagonal values (which are 0), our result is going to be at the top right corner 
(or dp[0][n-1]) and we never access lower diagonal values. So we cannot fill the matrix with a normal traversal, we rather need to fill in diagonal manner. 
We fill the matrix using a variable len that stores differences between row and column indexes. We keep increasing len until it becomes n-1 (for the top right element)
![image](https://github.com/user-attachments/assets/a34a1434-8928-4a0b-ac4f-b91009d2c5be)

