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
