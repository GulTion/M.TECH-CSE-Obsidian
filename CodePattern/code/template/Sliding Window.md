---
code_type: template
---
# Sliding Window (Shrinkable)
```cpp
int i = 0, j = 0, ans = 0;
for (; j < N; ++j) {
    // CODE: use A[j] to update state which might make the window invalid
    for (; invalid(); ++i) { // when invalid, keep shrinking the left edge until it's valid again
        // CODE: update state using A[i]
    }
    ans = max(ans, j - i + 1); // the window [i, j] is the maximum window we've found thus far
}
return ans;
```



>[!gemini]+ Gemini
>The provided code demonstrates the sliding window algorithm that iterates through an array using two pointers, `i` and `j`, to find the maximum window with a valid state. It follows a "shrinkable" approach, where the window can shrink as long as it remains valid.
> 
> 1. **Initialize Pointers and Maximum Length:**
>    - `i` is the left edge of the sliding window, initially set to 0.
>    - `j` is the right edge of the sliding window, initially set to 0.
>    - `ans` stores the maximum length of a valid window found so far, initialized to 0.
> 
> 2. **Iterate and Check Validity:**
>    - For each element `A[j]`, check if the current window `[i, j]` is valid.
>    - If invalid:
>      - Increment `i` until the window becomes valid again, updating the state using `A[i]` as the left edge.
> 
> 3. **Update Maximum Length:**
>    - After checking validity, calculate the length of the current window as `j - i + 1`.
>    - Update `ans` to be the maximum of its current value and the current window length.
> 
> 4. **Advance Right Pointer:**
>    - Increment `j` to continue iterating and potentially expand the window.
> 
> 5. **Return Result:**
>    - After iterating through the entire array, `ans` holds the maximum length of a valid window found during the process. This value is returned as the result.
> 
> In summary, this code efficiently finds the maximum window with a valid state in an array by shrinking the left edge as necessary while expanding the right edge.
 