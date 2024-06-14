---
code_type: template
type:
---

### LCS Table Filling
Sure, here are the equations for the different cases in the Longest Common Subsequence (LCS) problem:

1. **Base Case:**
	1. $dp[i][0] = 0 \quad \text{for all } i \quad (0 \leq i \leq m)$
	2. $dp[0][j] = 0 \quad \text{for all } j \quad (0 \leq j \leq n)$

2. **Recursive Case:**
     $$dp[i][j] = dp[i-1][j-1] + 1 \quad \text{if } X[i-1] == Y[j-1]$$
     $$dp[i][j] = \max(dp[i-1][j], dp[i][j-1]) \quad \text{if } X[i-1] \neq Y[j-1]$$

```cpp
    for (int i = 1; i <= m; ++i) {
        for (int j = 1; j <= n; ++j) {
            if (X[i - 1] == Y[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }
```

### Printing the LCS

To reconstruct the LCS from the filled DP table, follow these steps and use the corresponding equations:

1. **Initialization:**
   - Start from the bottom-right corner of the DP table:
    $$ i = m, \quad j = n $$

2. **Reconstruction Loop:**
   - While `i > 0` and `j > 0`:
     - If the characters match:
       $$
       \text{if } X[i-1] == Y[j-1] \text{ then } \text{LCS}[k] = X[i-1], \quad \text{decrement } i, j, \text{ and } k
       $$
     - If the characters do not match:
       - Move in the direction of the maximum value:
        $\text{if } dp[i-1][j] > dp[i][j-1] \text{ then } \text{decrement } i$
		$\text{else } \text{decrement } j$
```cpp
    int i = m, j = n;
    while (i > 0 && j > 0) {
        // If current character in X and Y are same, then it is part of LCS
        if (X[i - 1] == Y[j - 1]) {
            lcs[--index] = X[i - 1]; // Put current character in result
            --i;
            --j;
        }
        // If not the same, find the larger of two and go in the direction of the larger value
        else if (dp[i - 1][j] > dp[i][j - 1]) {
            --i;
        } else {
            --j;
        }
    }
```


