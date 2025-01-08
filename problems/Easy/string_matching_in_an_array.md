# Problem: 1408, String Matching in an Array
- **Difficulty**: Easy
- **Problem Link**: [LeetCode](https://leetcode.com/problems/string-matching-in-an-array/)

## Problem
Given an array of string words, return all strings in words that is a substring of another word. You can return the answer in any order.

A substring is a contiguous sequence of characters within a string

#### Constraints:

1 <= words.length <= 100

1 <= words[i].length <= 30

words[i] contains only lowercase English letters.

All the strings of words are unique.

## Overview of My solution
반복문을 돌 때마다 words의 복사본 words_copy을 새로 만든 후 word를 제외시키고,

word를 제외한 나머지 값들이 있는 words_copy에서 반복문을 돌면서 word가 substring이면 break한다.

## Solution
```python
class Solution:
    def stringMatching(self, words: List[str]) -> List[str]:
        results = []

        for word in words:
            words_copy = words[:]
            words_copy.remove(word)

            for word_copy in words_copy:
                if word in word_copy:
                    results.append(word)
                    break

        return results
```
## Complexity Analysis

- **Time Complexity**: $O(n^2)$ | $n$: 리스트의 길이

- **Space Complexity**: $O(n)$ 

## Points for Improvement

### 1. words_copy 리스트 복사의 비효율성
리스트 복사 없이, 조건문으로 현재 단어를 제외하고 비교할 수 있다.
```python
for word in words:
    for word_copy in words:
        if word != word_copy and word in word_copy: # word와 word_copy가 같으면 안되고 word가 substring이어야 함
            results.append(word)
            break
```

### 2. 중복된 결과 처리 
만약 words에 같은 값이 있었다면, results도 같은 값이 중복되어 있었겠지만 All the strings of words are unique이기 때문에 result를 굳이 set로 바꿀 필요는 없다.
(Points for Improvement에 넣은 이유는 이 조건을 전혀 생각하지 않았기 떄문)

## Improved Solution
```python
results = []
for word in words:
    for word_copy in words:
        if word != word_copy and word in word_copy:
            results.append(word)
            break
```

## Improved Complexity Analysis

- **Time Complexity**: $O(n^2)$

시간 복잡도는 여전히 $O(n^2)$로 유지되지만, 리스트 복사 및 삭제 과정이 제거되었기 때문에 실제 실행 시간은 이전보다 더 효율적이다.

- **Space Complexity**: $O(n)$

공간 복잡도는 여전히 $O(n)$로 나타나지만, 리스트 복사가 없어짐에 따라 추가적인 메모리 사용이 줄어들어 효율성이 개선되었다.

## Questions

1. 시간 복잡도를 $O(n^2)$보다 낮추는 방법이 있을까?
