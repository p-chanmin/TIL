> https://leetcode.com/problems/group-anagrams



# LeetCode : 49. Group Anagrams﻿

﻿

: Given an array of strings strs, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**: 주어진 문자열을 애너그램 단위로 그룹화 하라. 그 답은 어떤 순서로든 반환할 수 있다.**

**애너그램은 문장의 다른 단어나 구문을 재정렬하여 만들어진 단어나 구문으로 일반적으로 원문을 한 번만 사용함.**



***애너그램**

**일종의 언어유희로 문자를 재배열하여 다른 뜻을 가진 단어로 바꾸는 것을 말한다.**



**Example 1:**

```python
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

**Example 2:**

```python
Input: strs = [""]
Output: [[""]]
```

**Example 3:**

```python
Input: strs = ["a"]
Output: [["a"]]
```



**Constraints:**

1 <= strs.length <= 104

0 <= strs[i].length <= 100

strs[i] consists of lower-case English letters.

---



**Submissions Code:**

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        
        anagrams = collections.defaultdict(list)

        for word in strs:
            anagrams[''.join(sorted(word))].append(word)

        
        return list(anagrams.values())
```

anagrams라는 디폴트 딕셔너리를 생성한다. 이때 리스트를 값으로 하도록 한다.

strs의 문자열을 sorted로 정렬하여, .join으로 다시 문자열로 합친 값을 key로 한다.

같은 애너그램 그룹이라면 각 단어를 정렬했을 때, 똑같은 결과를 갖게 되므로, 정렬값을 key키로 리스트에 추가한다. 그리고 anagrams.values()를 통해 값만 추출하고 이를 리스트형으로 변형하여 반환한다.



**Using Keyword**

collections.defaultdict() - 디폴트 딕셔너리 생성.

sorted(자료) - 문자열, 리스트 등을 정렬하여 리스트로 반환.

''.join() - 리스트 값을 문자열로 합칠 때 사용.

dict.values() - 딕셔너리에서 값만 추출.



﻿