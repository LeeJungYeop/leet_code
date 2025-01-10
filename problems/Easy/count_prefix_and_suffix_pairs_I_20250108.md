# Problem: 3042, Count Prefix and Suffix Pairs I
- **Difficulty**: Easy
- **Problem Link**: [LeetCode](https://leetcode.com/problems/count-prefix-and-suffix-pairs-i/)
- **Status**: Thought Through(Solved by myself)

## Problem
You are given a 0-indexed string array words.

Let's define a boolean function isPrefixAndSuffix that takes two strings, str1 and str2:

isPrefixAndSuffix(str1, str2) returns true if str1 is both a prefix and a suffix of str2, and false otherwise.

For example, isPrefixAndSuffix("aba", "ababa") is true because "aba" is a prefix of "ababa" and also a suffix, but isPrefixAndSuffix("abc", "abcd") is false.

Return an integer denoting the number of index pairs (i, j) such that i < j, and isPrefixAndSuffix(words[i], words[j]) is true.

#### Constraints:

1 <= words.length <= 50

1 <= words[i].length <= 10

words[i] consists only of lowercase English letters.

## Overview of My solution

for문에서 index가 1만큼씩 커지고 words의 길이 만큼 반복하는데, 

words[i]가 words[i] 보다 뒤에 있는 값들 중에 prefix, suffix 관계를 둘 다 만족할 때마다 result를 증가시킨다.

## Solution
```python
class Solution:
    def countPrefixSuffixPairs(self, words: List[str]) -> int:
        result = 0

        for i in range(len(words)):
            for word in words[i+1:]:
                
                if words[i] == word:
                    result += 1

                else:
                    if word.startswith(words[i]) and word.endswith(words[i]):
                        result += 1

        return result
```
## Complexity Analysis

- **Time Complexity**: $O(n^2*m)$ | $n$: 리스트의 길이, $m$: 단어의 최대 길이 

- **Space Complexity**: $O(1)$ 

