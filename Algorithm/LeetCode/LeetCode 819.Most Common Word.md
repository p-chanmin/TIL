> https://leetcode.com/problems/most-common-word/



# ﻿LeetCode : 819. Most Common Word﻿

﻿

: Given a string paragraph and a string array of the banned words banned, return *the most frequent word that is not banned*. It is **guaranteed** there is **at least one word** that is not banned, and that the answer is **unique**.

The words in paragraph are **case-insensitive** and the answer should be returned in **lowercase**.



**: 문자열과 금지된 단어가 주어지면, 금지된 단어를 제외한 가장 흔하게 등장하는 단어를 출력하라.**

**금지되지 않은 단어는 최소 한 개이상 있으며, 답은 유일하다.**

**대소문자 구분을 하지 않으며, 답은 소문자로 반환해야 한다.**



**Example 1:**

```python
Input: paragraph = "Bob hit a ball, the hit BALL flew far after it was hit.", banned = ["hit"]
Output: "ball"
Explanation: 
"hit" occurs 3 times, but it is a banned word.
"ball" occurs twice (and no other word does), so it is the most frequent non-banned word in the paragraph. 
Note that words in the paragraph are not case sensitive,
that punctuation is ignored (even if adjacent to words, such as "ball,"), 
and that "hit" isn't the answer even though it occurs more because it is banned.
```

**Example 2:**

```python
Input: paragraph = "a.", banned = []
Output: "a"
```



**Constraints:**

1 <= paragraph.length <= 1000

paragraph consists of English letters, space ' ', or one of the symbols: "!?',;.".

0 <= banned.length <= 100

1 <= banned[i].length <= 10

banned[i] consists of only lowercase English letters.

---



**Submissions Code:**

```python
class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:
        paragraph = paragraph.lower()
        
        paragraph = re.sub('[^a-z]',' ',paragraph)
        
        words = paragraph.split()
        
        for ban in banned:
            while(ban in words):
                words.remove(ban)
        
        m = 0
        word = None
        for i in set(words):
            if m < words.count(i):
                word = i
                m = words.count(i)
                
        return word
```

먼저 대소문자를 구분하지 않으므로 lower()을 사용하여 소문자로 바꾼다.

re.sub('`[^a-z]`',' ',paragraph)를 통해서 소문자 알파벳을 제외한 값을 공백1칸으로 변경한다.

그리고 words = paragraph.split() 를 통해서 단어들을 words 리스트에 저장한다.



반복문을 돌면서 banned 안의 금지 단어들을 words 에서 제외시킨다.

마지막으로 set을 사용하여 단어들 중에서 가장 빈도가 높은 단어를 반환한다.



**Other Submissions Code:**

**- Using Counter**

```python
class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:
        
        words = [word for word in re.sub('[^\w]',' ',paragraph).lower().split() if word not in banned]
        
        counts = collections.Counter(words)
                
        return counts.most_common(1)[0][0]
```

words = [word for word in re.sub('[^\w]',' ',paragraph).lower().split() if word not in banned]

이 한 문장으로 금지 단어를 제외한 단어를 words 에 저장할 수 있다.

Counter를 사용하여 각 words 안에 있는 단어와 빈도를 저장할 수 있는데, 여기서

most_common(k)를 사용하면 가장 빈도가 높은 k개를 반환한다. 따라서 가장 빈도가 높은 1개를 반환하면

[('ball', 2)]인데 여기서 `[0][0]`을 통해 최종적으로 가장 빈도가 높은 단어를 반환하게 된다.



**Using Keyword**

re. sub(정규식, 바꿀문자, 검색 문자열)

list.remove(값) - 리스트 안에서 값에 해당하는 데이터를 지움.

'\w' - 정규표현식에서 단어 문자를 의미, 따라서 ^(not)과 함께 '^\w'는 단어 문자가 아닌 모든 문자의 의미

collections.Counter(list) - 리스트에서 값과 빈도수를 함께 저장하는 counter

counter.most_common(k) - 가장 빈도가 높은 k개의 데이터의 값과 빈도수를 반환한다.



﻿