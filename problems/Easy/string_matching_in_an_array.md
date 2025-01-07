# Problem: 1408, String Matching in an Array
- **Difficulty**: Easy
- **Problem Link**: [LeetCode](https://leetcode.com/problems/string-matching-in-an-array/)

## Solution
class Solution:
    def stringMatching(self, words: List[str]) -> List[str]:
        results = []

        for word in words:
            words_copy = words[:]
            words_copy.remove(word)
            print(words_copy)

            for word_copy in words_copy:
                if word in word_copy:
                    results.append(word)
                    break

        return results
