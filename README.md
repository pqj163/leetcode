# leetcode

1. [937 - Reorder Data in Log Files
](#---937)
2. [344 - Reverse String](#---344)
3. [819 - Most Common Word](#---819)
4. [49 -  Group Anagrams](#---49)

## 【[ § ](#leetcode)】 937
> **Reorder Data in Log Files**   
[[문제](https://leetcode.com/problems/reorder-data-in-log-files/)] 

|  일자  |시도|참고|예시|정답|시간|공간|  §  | 
|  :--:  |:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|21-01-12| 2  | X  | O  | O  | 1  | 2  | [[ § 937-1 ](#-----937----1)] |
|21-01-12| 3  | O  | O  | O  | 2  | 1  | [[ § 937-2 ](#-----937----2)] |

### 【[ § ](#leetcode)】 [[ § 937 ](#---937)] - 1 
첫번째 시도 때 문자열을 리스트를 보고 쪼갠 다음 리스트의 요소로 정렬한 것 까지는 똑같았는데, 2번째 요소로만 정렬했었다가 2번째 요소는 같은데 3번째 요소는 다른 로그가 인풋으로 들어와서 틀렸다.
```Python
class Solution(object):
    def reorderLogFiles(self, logs):
        """
        :type logs: List[str]
        :rtype: List[str]
        """
        str_li = []
        num_li = []
        results = []
        for log in logs:
            li_log = log.split(" ")
            try:
                int(li_log[1])
                num_li.append(" ".join(li_log))
            except:
                str_li.append(li_log)
        str_li.sort(key = lambda x:x[0])
        str_li.sort(key = lambda x:x[1:])
        for li_log in str_li:
            results.append(" ".join(li_log))
        
        return results + num_li
```
- 결과
```
Runtime: 24 ms, faster than 74.06% of Python online submissions for Reorder Data in Log Files.
Memory Usage: 13.9 MB, less than 7.50% of Python online submissions for Reorder Data in Log Files.
```

### 【[ § ](#leetcode)】 [[ § 937 ](#---937)] - 2 
이번에는 책을 따라해봤다. isdigit()을 활용할 생각도 못했고, 굳이 쪼개서 배열에 넣을 필요가 없을 것이라는 것도 생각못했다. 근데 이쪽 코드가 더 짧아서 속도가 이쪽이 더 빠를 것이라 생각했는데, 그렇지는 않더라. 1번에서는 공간을 더 쓴 대신 조금 더 빨랐고, 2번에서는 조금 느린 대신 공간을 덜 썼다.
```Python
class Solution(object):
    def reorderLogFiles(self, logs):
        """
        :type logs: List[str]
        :rtype: List[str]
        """
        str_li = []
        num_li = []
        
        for log in logs :
            if log.split()[1].isdigit():
                num_li.append(log)
            else:
                str_li.append(log)
        str_li.sort(key=lambda x: (x.split()[1:],x.split()[0]))
        
        return str_li+num_li
```

- 결과
```
Runtime: 28 ms, faster than 44.69% of Python online submissions for Reorder Data in Log Files.
Memory Usage: 13.7 MB, less than 55.41% of Python online submissions for Reorder Data in Log Files.
```

## 【[ § ](#leetcode)】 344
> **Reverse String **  
[[문제](https://leetcode.com/problems/reverse-string/)] 

|  일자  |시도|참고|예시|정답|시간|공간|  §  | 
|  :--:  |:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|21-01-12| 1  | O  | O  | O  | 1  | 1  | [[ § 344-1 ](#-----344----1)] |

### 【[ § ](#leetcode)】 [[ § 344 ](#---344)] - 1
사실 이건 책에서 답을 이미 봐서 답이 뭔지 알았는데, s=s[::-1]은 공간복잡도 1을 초과해서 안되지만 아래의 코드에 나온 예시는 된다기에, 내 생각에 s[:]는 문자열을 복사한 것이니 복사한 문자열에 뒤집힌 문자열을 할당하면 복사한 문자열은 어디에도 할당되지 않았으니 사라지는 것이 아닌가, 그렇다면 이건 답이 될 수 없는 거 아닌가 싶어서 해봤다. 근데 되더라. 문자열을 복사한 다음 따로 할당을 안해주면 s의 주소값이랑 연결되게 되어 있나...? 나중에 더 알아봐야겠다.
아니 근데 이거보다 빠른 답은 도대체 뭐람..?
```Python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        s[:] = s[::-1]
```
- 결과
```
Runtime: 164 ms, faster than 78.23% of Python online submissions for Reverse String.
Memory Usage: 21 MB, less than 83.14% of Python online submissions for Reverse String.
```

## 【[ § ](#leetcode)】 819
> **Most Common Word**   
[[문제](https://leetcode.com/problems/most-common-word/)] 

|  일자  |시도|참고|예시|정답|     시간    |    공간   |  §  | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-12| 3  | △ | O  | O  | 2 (12.82%) | 1 (40.38%) | [[ § 819-1 ](#-----819----1)] |
|21-01-12| 4  | O  | O  | O  | 1 (54.38%) | 2 (14.74%) | [[ § 819-2 ](#-----819----2)] |

### 【[ § ](#leetcode)】 [[ § 819 ](#---819)] - 1 
첫번째 시도 때 strip()으로,랑 .만 지우고 !를 남겨서 실패했고, 두번째는 띄어쓰기 없이 ,b,b 이런 식으로 붙어있는 문자열 때문에 split()이 이상하게 돼서 실패했다. 참고를 아예 안했다기에는 Counter를 애초에 책보고 배우기도 했고, 밑에 제목을 언뜻 봤는데 대놓고 Counter랑 리스트 컴프리헨션이 써있어서 답은 안봤지만 참고를 아예 안했다고 하긴 뭐해서 세모로 했다...
```Python
class Solution(object):
    def mostCommonWord(self, paragraph, banned):
        """
        :type paragraph: str
        :type banned: List[str]
        :rtype: str
        """
        
        paragraph = paragraph.lower()
        
        for i, al in enumerate(paragraph):
            if not al.isalpha() and al !=" ":
                paragraph = paragraph.replace(paragraph[i]," ")
        
        counts = collections.Counter(paragraph.split())
        
        for ban in banned:
            try:
                del counts[ban]
            except:
                pass
        
        return counts.most_common()[0][0]
```
- 결과
```
Runtime: 40 ms, faster than 12.82% of Python online submissions for Most Common Word.
Memory Usage: 13.7 MB, less than 40.38% of Python online submissions for Most Common Word.
```

### 【[ § ](#leetcode)】 [[ § 819 ](#---819)] - 2 
책을 보고 따라해봤는데, 정규 표현식이 따로 안나왔으니 안쓰겠거니 했는데 바로 쓰더라... 이렇게 하니 코드가 보기에 불편할지언정 훨 간결해졌다. 속도는 빨라졌지만 공간을 조금 더 많이 잡아먹는다. 근데 속도가 이 정도 차이면 충분히 희생할만한 공간이지 싶다. 근데 공간은 어떤 식으로 측정되는 거지...? 스택에 쌓이는 정도?
```Python
class Solution(object):
    def mostCommonWord(self, paragraph, banned):
        """
        :type paragraph: str
        :type banned: List[str]
        :rtype: str
        """
        
        words = [word for word in re.sub(r'[^\w]', ' ', paragraph)
                 .lower().split() 
                 if word not in banned]
        
        counts = collections.Counter(words)
        
        return counts.most_common()[0][0]
```
- 결과
```
Runtime: 28 ms, faster than 54.38% of Python online submissions for Most Common Word.
Memory Usage: 13.8 MB, less than 14.74% of Python online submissions for Most Common Word.
```

## 【[ § ](#leetcode)】 49
> **Group Anagrams**   
[[문제](https://leetcode.com/problems/group-anagrams/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-12| 3  | X  | O  | O  | 2 (5.01%)  | 2 (26.84%) | [[ § 49-1 ](#-----49----1)] |
|21-01-12| 4  | O  | O  | O  | 1 (98.72%) | 1 (57.46%) | [[ § 49-2 ](#-----49----2)] |

### 【[ § ](#leetcode)】 [[ § 49 ](#---49)] - 1 
처음에 '아마 겹치는 숫자 있어서 안되지 싶은데...' 하면서도 유니코드 변환 후 합산해서 비교한 다음 리스트를 만들어 주는 식으로 했었는데 아니나 다를까 겹치는 숫자가 있어서 실패했다. 그 다음은 집합으로 뭘 어떻게 해보려 했는데 계속 에러가 나기도 하고, 같은 알파벳이 2개인 단어와 다른 1개인 단어가 겹칠까 싶어 결국 지금 방식이 됐다. 근데 시간이 너무 긴데..?
```Python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        
        words_dict = {}
        results = []
        
        for word in strs:
            temp = tuple(sorted([a for a in word])) 
            if temp not in words_dict.keys():
                words_dict[temp] = []
            words_dict[temp].append(word)
        
        for li in words_dict.values():
            results.append(li)
            
        return results
```
- 결과
```
Runtime: 2196 ms, faster than 5.01% of Python online submissions for Group Anagrams.
Memory Usage: 18.2 MB, less than 26.84% of Python online submissions for Group Anagrams.
```

### 【[ § ](#leetcode)】 [[ § 49 ](#---49)] - 2 
책을 봤는데 방향이 크게 다르지 않은 것 같아서 성능 차이가 별로 안나면 그냥 따로 기록을 안하려고 했다. 근데 많이 나더라... 혹시 .values()로 바로 리턴을 안하고 리스트에 추가한 다음에 리턴해서 그런가 싶어 위에 것을 수정해서 해봤는데 오히려 더 느려졌다... 그나저나 바보같이 바로 리턴할 생각을 못했구나 싶다. 그리고 사실 1번에서도 defaultdict를 써보려 했는데 잘 안됐다. append가 안되더라. 지금보니 괄호에 list를 적어서 기본값을 정해줬어야 하는 모양이다.
```Python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        
        ana = collections.defaultdict(list)
        
        for word in strs:
            ana[''.join(sorted(word))].append(word)
        return ana.values()
```
- 결과
```
Runtime: 72 ms, faster than 98.72% of Python online submissions for Group Anagrams.
Memory Usage: 17.6 MB, less than 57.46% of Python online submissions for Group Anagrams.
```

