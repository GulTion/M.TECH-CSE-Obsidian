---
tags:
  - "#Stack"
code_type: "[[identification]]"
---
1. `Array` will be given
2. time complexity will be $O(n^2)$ 
3. brute force solution will contains two dependent loops e.g.
```cpp
for(int i=0;i<n;i++)
	for(int j=i;j<n;j++)
	// OR
	for(int j=n;j<i;j--)
	// OR
	for(int j=0;j<i;j++)
	// OR
	for(int j=i;j>0;j--)
```
