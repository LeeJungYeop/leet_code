# Problem: 916, Word Subsets
- **Difficulty**: Medium
- **Problem Link**: [LeetCode](https://leetcode.com/problems/word-subsets)
- **status**: No Approach(Solved by ChatGPT)

## Problem
You are given two string arrays words1 and words2.

A string b is a subset of string a if every letter in b occurs in a including multiplicity.

For example, "wrr" is a subset of "warrior" but is not a subset of "world".

A string a from words1 is universal if for every string b in words2, b is a subset of a.

Return an array of all the universal strings in words1. You may return the answer in any order.

#### Constraints:

1 <= words1.length, words2.length <= 104

1 <= words1[i].length, words2[i].length <= 10

words1[i] and words2[i] consist only of lowercase English letters.

All the strings of words1 are unique.

## Overview of solution

words2의 모든 문자열에 대해 필요한 최소 문자 개수를 max_count에 저장한 후, 

words1에서 max_count에 저장된 최소 문자 개수 이상을 가지고 있는 문자들만 result에 저장한다.

## Solution
```python
from collections import Counter
from typing import List

class Solution:
    def wordSubsets(self, words1: List[str], words2: List[str]) -> List[str]:
        max_count = Counter()
        for word in words2:
            word_count = Counter(word)
            for char in word_count:
                max_count[char] = max(max_count[char], word_count[char])
        
        # words1의 각 단어가 조건을 만족하는지 확인
        results = []
        for word in words1:
            word_count = Counter(word)
            # 모든 문자가 max_count 조건을 만족하는지 확인
            if all(word_count[char] >= max_count[char] for char in max_count):
                results.append(word)
        
        return results
```
## Complexity Analysis

- **Time Complexity**: $O((n+m)L)$ | $n$: words1의 길이, $m$: words2의 길이, $L$: 단어의 평균 길이

- **Space Complexity**: $O(n)$ 
