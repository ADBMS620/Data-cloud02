---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---

# Longest Common Subsequence (LCS)

Given two strings, **s1** and **s2**, the task is to find the length of the **Longest Common Subsequence**. If there is no **common subsequence**, return **0**. A **subsequence** is a string that is derived from the original string by deleting 0 or more characters, without changing the relative order of the remaining characters.

For example, subsequences of **"ABC"** are “”, “A”, “B”, “C”, “AB”, “AC”, “BC” and “ABC”. In general, a string of length **n** has $2^n$ subsequences.

**Examples**
```plaintext
Input: s1 = “ABC”, s2 = “ACD”
Output: 2
Explanation: The longest subsequence which is present in both strings is “AC”.


Input: s1 = “AGGTAB”, s2 = “GXTXAYB”
Output: 4
Explanation: The longest common subsequence is “GTAB”.


Input: s1 = “ABC”, s2 = “CBA”
Output: 1
Explanation: There are three longest common subsequences of length 1, “A”, “B” and “C”.
```

## Table of Content

- [Naive Approach] Using Recursion – O(2 ^ min(m, n)) Time and O(min(m, n)) Space
- [Better Approach] Using Memoization – O(m * n) Time and O(m * n) Space
- [Expected Approach 1] Using Bottom-Up DP (Tabulation) – O(m * n) Time and O(m * n) Space
- [Expected Approach 2] Using Bottom-Up DP (Space-Optimization):
- Applications of LCS

 ## [Naive Approach] Using Recursion – O(2 ^ min(m, n)) Time and O(min(m, n)) Space
 
The idea is to compare the last characters of **s1** and **s2**. While comparing the strings **s1** and **s2** two cases arise:

1. **Match :** Make the recursion call for the remaining strings (strings of lengths **m-1** and **n-1**) and add **1** to result.
2. **Do not Match :** Make two recursive calls. First for lengths m-1 and n, and second for m and n-1. Take the maximum of two results.

**Base case :** If any of the strings become empty, we return 0.


**For example**, consider the input strings s1 = “ABX” and s2 = “ACX”.
```plainetext
LCS(“ABX”, “ACX”) = 1 + LCS(“AB”, “AC”) [Last Characters Match]


 LCS(“AB”, “AC”) = max( LCS(“A”, “AC”) , LCS(“AB”, “A”) ) [Last Characters Do Not Match] 


LCS(“A”, “AC”) = max( LCS(“”, “AC”) , LCS(“A”, “A”) ) = max(0, 1 + LCS(“”, “”)) = 1


LCS(“AB”, “A”) = max( LCS(“A”, “A”) , LCS(“AB”, “”) ) = max( 1 + LCS(“”, “”, 0)) = 1


So overall result is 1 + 1 = 2
```

## [Better Approach] Using Memoization (Top Down DP) – O(m * n) Time and O(m * n) Space

To optimize the recursive solution, we use a **2D memoization table** of size $(m+1)×(n+1)(m+1)$ \times $(n+1)(m+1)×(n+1)$, initialized to $−1-1−1$ to track computed values. Before making recursive calls, we check this table to avoid redundant computations of overlapping subproblems. This prevents repeated calculations, improving efficiency through **memoization or tabulation.**
![Longest Common Subsequence 1](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest-Common-Subsequence%201.jpeg?raw=true)



## [Expected Approach 1] Using Bottom-Up DP (Tabulation) – O(m * n) Time and O(m * n) Space

There are two parameters that change in the recursive solution and these parameters go from 0 to m and 0 to n. So we create a 2D dp array of size (m+1) x (n+1).  


- We first fill the known entries when m is 0 or n is 0.
- Then we fill the remaining entries using the recursive formula.

Say the strings are **S1 = “AXTY”** and **S2 = “AYZX”**, Follow below :


![Step 1](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest-Common-Subsequence%202.jpeg?raw=true)
![Step 2](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest-Common-Subsequence%203.jpeg?raw=true)
![Step 3](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest%20Common%20Subsequence%204.jpeg?raw=true)
![Step 4](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest%20Common%20Subsequence%205.jpeg?raw=true)
![Step 5](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/longest-common-subsequence/Longest%20Common%20Subsequence%206.jpeg?raw=true)

## [Expected Approach 2] Using Bottom-Up DP (Space-Optimization):
One important observation in the above simple implementation is, in each iteration of the outer loop we only need values from all columns of the previous row. So there is no need to store all rows in our DP matrix, we can just store two rows at a time and use them. We can further optimize to use only one array.

**Applications of LCS**

LCS is used to implement diff utility (find the difference between two data sources). It is also widely used by revision control systems such as Git for multiple changes made to a revision-controlled collection of files.



