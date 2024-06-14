---
{}
---



## Solution 1. Brute Force

```cpp
// OJ: https://leetcode.com/problems/count-vowel-substrings-of-a-string/
// Author: github.com/lzl124631x
// Time: O(N^2)
// Space: O(1)
class Solution {
    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    };
public:
    int countVowelSubstrings(string s) {
        int ans = 0, N = s.size();
        unordered_map<char, int> cnt;
        for (int i = 0; i < N; ++i) {
            cnt.clear();
            for (int j = i; j < N && isVowel(s[j]); ++j) {
                cnt[s[j]]++;
                if (cnt.size() == 5) ++ans;
            }
        }
        return ans;
    }
};
```

## Solution 2. Sliding Window

Check out "[[C++ Maximum Sliding Window Cheatsheet Template!]]"

Function `atMost(s, goal)` returns the number of substrings that has at most `goal` number of unique vowels. The answer is `atMost(s, 5) - atMost(s, 4)`.

```cpp
// OJ: https://leetcode.com/problems/count-vowel-substrings-of-a-string/
// Author: github.com/lzl124631x
// Time: O(N)
// Space: O(1)
class Solution {
    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    };
    int atMost(string &s, int goal) {
        int ans = 0, i = 0, j = 0, N = s.size();
        unordered_map<char, int> cnt;
        for (; j < N; ++j) {
            if (!isVowel(s[j])) {
                i = j + 1;
                cnt.clear();
                continue;
            }
            cnt[s[j]]++;
            for (; cnt.size() > goal; ++i) {
                if (--cnt[s[i]] == 0) cnt.erase(s[i]);
            }
            ans += j - i + 1; // this window [i, j] is the maximum window ending at `s[j]` that has at most `goal` number of unique vowels.
        }
        return ans;
    }
public:
    int countVowelSubstrings(string s) {
        return atMost(s, 5) - atMost(s, 4);
    }
};
```

![[🌟 Sliding Window "At Most to Equal" trick]]