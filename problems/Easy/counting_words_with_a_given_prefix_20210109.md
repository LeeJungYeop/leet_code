# Problem: 2185, Counting Words With a Given Prefix
- **Difficulty**: Easy
- **Problem Link**: [LeetCode](https://leetcode.com/problems/counting-words-with-a-given-prefix/)

## Problem
You are given an array of strings words and a string pref.

Return the number of strings in words that contain pref as a prefix.

A prefix of a string s is any leading contiguous substring of s.

#### Constraints:

1 <= words.length <= 100

1 <= words[i].length, pref.length <= 100

words[i] and pref consist of lowercase English letters.

## Overview of My solution

for문에서 word가 pref로 시작되면, result를 1만큼 증가시킨다.

## Solution
```python
class Solution:
    def prefixCount(self, words: List[str], pref: str) -> int:
        result = 0 

        for word in words:
            if word.startswith(pref):
                result += 1
        
        return result
```
## Complexity Analysis

- **Time Complexity**: $O(n*m)$ | $n$: 리스트의 길이, $m$: 단어의 최대 길이 

- **Space Complexity**: $O(1)$ 

