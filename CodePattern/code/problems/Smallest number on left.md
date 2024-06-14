---
tags:
  - Stack
code_difficulty: medium
code_src: geeksforgeeks
code_type: problem
---
# Problem
Given an array **a** of integers of length **n**, find the nearest smaller number for every element such that the smaller element is on left side.If no small element present on the left print -1.

**Example 1:**

**Input:** n = 3
a = {1, 6, 2}
**Output:** -1 1 1
**Explaination:** There is no number at the 
left of 1. Smaller number than 6 and 2 is 1.

**Example 2:**

**Input:** n = 6
a = {1, 5, 0, 3, 4, 5}
**Output:** -1 1 -1 0 3 4
**Explaination:** Upto 3 it is easy to see 
the smaller numbers. But for 4 the smaller 
numbers are 1, 0 and 3. But among them 3 
is closest. Similary for 5 it is 4.

**Your Task:**  
You do not need to read input or print anything. Your task is to complete the function **leftSmaller()** which takes n and a as input parameters and returns the list of smaller numbers.

**Expected Time Complexity:** O(n)  
**Expected Auxiliary Space:** O(n)

**Constraints:**  
1 ≤ n ≤ 10000  
0 ≤ a[i] ≤ 104

# Solution

```cpp
vector<int> leftSmaller(int n, int a[]){
        stack<int> s;
        vector<int> v(n,-1);
	    
	    for(int i=0;i<n;i++){
	        while(!s.empty()&&s.top()>=a[i]) s.pop();
	        if(!s.empty()) v[i] = s.top();
	        s.push(a[i]);
	    }
	    
	    return v;
    }
```



>[!gemini]+ Gemini
>The provided C++ code efficiently addresses the problem of finding the nearest smaller number for each element in an array, ensuring that the smaller number is on the left. It utilizes a stack data structure and operates in a single pass through the array.
> 
> **Approach:**
> 
> 1. **Stack for Storing Elements:** A stack is used to store elements from the array.
> 2. **Loop Through the Array:** Iterate through each element in the array.
> 3. **Pop Elements Smaller Than the Current Element:** While the stack is not empty and the top element is greater than or equal to the current element, pop the top element from the stack.
> 4. **Nearest Smaller Element:** If the stack is not empty, the top element represents the nearest smaller number for the current element.
> 5. **Push Current Element:** Push the current element onto the stack.
> 6. **Populate the Result Vector:** Store the nearest smaller number for each element in a vector. If no smaller number is found, assign -1 to that element.
> 
> **Complexity Analysis:**
> 
> * **Time Complexity:** O(N), where N is the number of elements in the array. A single pass through the array is performed, and each element is processed only once.
> * **Space Complexity:** O(N), as the stack and the result vector can both store up to N elements in the worst case.
> 
> **Example Usage:**
> 
> ```cpp
> int main() {
>   int n = 6;
>   int a[] = {1, 5, 0, 3, 4, 5};
>   vector<int> result = leftSmaller(n, a);
>   for (int x : result) cout << x << " ";
   return 0;
 }
```
> 
> **Output:**
> 
> ```
> -1 1 -1 0 3 4
> ```
 