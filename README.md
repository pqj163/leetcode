# leetcode

#### - 문자열 [[↓]](#문자열-)
1. 
2. [937. Reorder Data in Log Files](#---937-)
3. [344. Reverse String](#---344-)
4. [819. Most Common Word](#---819-)
5. [49.  Group Anagrams](#---49-)
6. [5. Longest Palindromic Substring](#---5-)
#### - 배열 [[↓]](#배열-)
7. [1. Two Sum](#---1-)
8. [42. Trapping Rain Water](#---42-)
9. [15. 3Sum](#---15-)
10. 
11. 
12. 
#### - 연결 리스트 [[↓]](#연결-리스트-)
13. [234. Palindrome Linked List](#---234-)
14. [21. Merge Two Sorted Lists](#---21-)
15. [206. Reverse Linked List](#---206-)
16. [2. Add Two Numbers](#---2-)
17. [24. Swap Nodes in Pairs](#---24-)
18. [328. Odd Even Linked List](#---328-)
19. [92. Reverse Linked List II](#---92-)
#### - 스택, 큐 [[↓]](#스택-큐-)
20. [20. Valid Parentheses](#---20-)
21. -
22. -
23. -
24. -
25. -
#### - 데크, 우선순위 큐 [[↓]](#데크-우선순위-큐-)
26. -
27. -
#### - 해시 테이블 [[↓]](#해시-테이블-)
28. -
29. [771. Jewels and Stones](#---771-)
30. -
31. [347. Top K Frequent Elements](#---347-)
#### - 그래프 [[↓]](#그래프-)
32. -
33. -
34. -
35. [77. Combinations](#---77-)
36. [39. Combination Sum](#---39-)
37. -
38. -
39. [207. Course Schedul](#---207-)
#### - 최단 경로 문제 [[↓]](#최단-경로-문제-)
40.  -
41.  -
#### - 트리 [[↓]](#트리-)
42.  [104. Maximum Depth of Binary Tree](#---104-)
43.  -
44.  [687. Longest Univalue Path](#---687-)
45.  [226. Invert Binary Tree](#---226-)
46.  -
47.  -
48.  -
49.  -
50.  -
51.  -
52.  -
53.  -
54.  -
#### - 힙 [[↓]](#힙-)
1.   -
#### - 트라이 [[↓]](#트라이-)
1.   -
2.   -

# 문자열 [[↑]](#--문자열-)

## 【[ § ](#leetcode)】 937 [[↑]](#문자열-)
> **Reorder Data in Log Files**   
[[문제](https://leetcode.com/problems/reorder-data-in-log-files/)] 

|  일자  |시도|참고|예시|정답|시간|공간|  §  | 
|  :--:  |:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|21-01-12| 2  | X  | O  | O  | 1  | 2  | [[ § 937-1 ](#-----937----1-)] |
|21-01-12| 3  | O  | O  | O  | 2  | 1  | [[ § 937-2 ](#-----937----2-)] |

### 【[ § ](#leetcode)】 [[ § 937 ](#---937-)] - 1 [[↑]](#문자열-)
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

### 【[ § ](#leetcode)】 [[ § 937 ](#---937-)] - 2 [[↑]](#문자열-)
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

## 【[ § ](#leetcode)】 344 [[↑]](#문자열-)
> **Reverse String **  
[[문제](https://leetcode.com/problems/reverse-string/)] 

|  일자  |시도|참고|예시|정답|시간|공간|  §  | 
|  :--:  |:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|21-01-12| 1  | O  | O  | O  | 1  | 1  | [[ § 344-1 ](#-----344----1-)] |

### 【[ § ](#leetcode)】 [[ § 344 ](#---344-)] - 1 [[↑]](#문자열-)
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

## 【[ § ](#leetcode)】 819 [[↑]](#문자열-)
> **Most Common Word**   
[[문제](https://leetcode.com/problems/most-common-word/)] 

|  일자  |시도|참고|예시|정답|     시간    |    공간   |  §  | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-12| 3  | △ | O  | O  | 2 (12.82%) | 1 (40.38%) | [[ § 819-1 ](#-----819----1-)] |
|21-01-12| 4  | O  | O  | O  | 1 (54.38%) | 2 (14.74%) | [[ § 819-2 ](#-----819----2-)] |

### 【[ § ](#leetcode)】 [[ § 819 ](#---819-)] - 1 [[↑]](#문자열-)
첫번째 시도 때 strip()으로,랑 .만 지우고 !를 남겨서 실패했고, 두번째는 띄어쓰기 없이 ,b,b 이런 식으로 붙어있는 문자열 때문에 split()이 제대로 안되서 실패했다. 참고를 아예 안했다기에는 Counter를 애초에 책보고 배우기도 했고, 밑에 소제목을 언뜻 봤는데 대놓고 Counter랑 리스트 컴프리헨션이 써있어서 답은 안봤지만 참고를 아예 안했다고 하긴 뭐해서 세모로 했다...
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

### 【[ § ](#leetcode)】 [[ § 819 ](#---819-)] - 2 [[↑]](#문자열-)
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

## 【[ § ](#leetcode)】 49 [[↑]](#문자열-)
> **Group Anagrams**   
[[문제](https://leetcode.com/problems/group-anagrams/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-12| 3  | X  | O  | O  | 2 (5.01%)  | 2 (26.84%) | [[ § 49-1 ](#-----49----1-)] |
|21-01-12| 4  | O  | O  | O  | 1 (98.72%) | 1 (57.46%) | [[ § 49-2 ](#-----49----2-)] |

### 【[ § ](#leetcode)】 [[ § 49 ](#---49-)] - 1 [[↑]](#문자열-)
처음에 '아마 겹치는 숫자 있어서 안되지 싶은데...' 하면서도 유니코드 변환 후 합산해서 비교한 다음 리스트를 만들어 주는 식으로 했었는데 아니나 다를까 겹치는 숫자가 있어서 실패했다. 그 다음은 집합으로 뭘 어떻게 해보려 했는데 계속 에러가 나기도 하고, 같은 알파벳이 2개인 단어와 다른 1개인 단어가 겹칠까 싶어 결국 지금 방식이 됐다. 근데 시간이 너무 긴데..?
> 2번과의 비교를 위해 defaultdict를 사용하는 것만 빼고 조건을 조금씩 바꿔가면서 해보니 다른 조건들은 시간이 조금씩은 줄어도 많이 줄 지는 않았는데 if문을 try, except로 바꾸니 2번과 유사한 성능이 나왔다. .keys()를 이용해 일일이 비교한 것이 문제였을까, if문 자체가 문제였을까?

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

### 【[ § ](#leetcode)】 [[ § 49 ](#---49-)] - 2 [[↑]](#문자열-)
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







## 【[ § ](#leetcode)】 5 [[↑]](#문자열-)
> **Longest Palindromic Substring**   
[[문제](https://leetcode.com/problems/longest-palindromic-substring/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-13| 9  | O  | O  | O  | 1 (94.42%)  | 1 (76.37%) | [[ § 5-1 ](#-----5----1-)] |

### 【[ § ](#leetcode)】 [[ § 5 ](#---5-)] - 1 [[↑]](#문자열-)
처음엔 뒤집어서 서로 다른 쪽에서, 또 서로 같은 쪽에서 비교해가면서 찾는 식으로 접근했는데, 이렇게 접근하니 코드를 수정해서 한 케이스를 통과하면 다음 케이스에서 틀리더라. 가령 펠린드롬이 아닌데 우연히 같은 인덱스에 같은 알파벳이 여러번 겹친 탓에 걔가 리턴된다던지... 내가 아는 지식들로는 해결이 힘들겠다 싶어 책을 봤는데 투 포인터 어쩌고 하길래 머리가 아파서 책을 도로 덮었다. 당최 뭔소린지 모르겠어서 안되겠거니하고 반즈음 포기하고 있었는데, 샤워를 하고 나니 갑자기 무슨 소리였는 지 이해가 됐다. 아, 그리고 오늘 스터디에서 현업자가 타입 지정이 굉장히 유용한 팁이라고 했다는 말을 듣고 해보려 했는데, 파이썬 버전 문제인지 뭔지 리트코드에서는 신택스 에러가 났다. 레플에서는 되는 거 보니 파이썬 버전 문제가 맞지 싶다. 비록 리트코드에서는 타입지정을 못해줬지만 여기서라도 해줘야지...
>21-01-15 : 가만보니 책에서 나온 방식과 다를지언정, 여기서도 타입힌트는 주고 있었다. 내가 '뭔 영어가 써있냐'하고 그냥 넘겨서 몰랐을 뿐...

```Python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """

        def expend(left: int, right: int) -> str:
            while 0 <= left and right <= len(s) and s[left] == s[right-1]:
                left -= 1
                right += 1
            return s[left + 1 : right - 1]
        
        if len(s) < 2 or s == s[::-1]:
            return s
        
        result = ''
        
        for i in range(len(s)-1):
            result = max(result,
                         expend(i,i+1),
                         expend(i,i+2),
                         key = len)
        return result
```
- 결과
```
Runtime: 240 ms, faster than 94.42% of Python online submissions for Longest Palindromic Substring.
Memory Usage: 13.5 MB, less than 76.37% of Python online submissions for Longest Palindromic Substring.
```

# 배열 [[↑]](#--배열-)

## 【[ § ](#leetcode)】 1 [[↑]](#배열-)
> **Two Sum**   
[[문제](https://leetcode.com/problems/two-sum/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 5  | X  | O  | O  | 1 (5.08%)  | 1 (12.13%) | [[ § 1-1 ](#-----1----1-)] |

### 【[ § ](#leetcode)】 [[ § 1 ](#---1-)] - 1 [[↑]](#배열-)
풀 때 상태가 안좋아서 '그래... 통과만 하자'하는 심정으로 풀었는데 솔직히 되게 쉬운 문제였는데 한번에 통과하지도 못했고 성능도 엉망이다... target이 나오는 단 하나의 경우를 리턴했어야 했는데, 처음에는 2가지 경우를 리턴하는 바람에 틀렸고, 그 다음에는 경우가 하나만 나타나도 바로 리턴하게 해놨더니 숫자가 하나만 리턴돼서 틀리기에 '이건 뭐지...?' 하고 그냥 아무렇게나 막 좀 해보다가 하나만 리턴되는 경우를 다시 살펴보니 그 숫자 하나만으로 target을 완성할 수 있는 경우더라... 그래서 자기 자신이 아니어야 하는 조건을 추가했다. 근데 이렇게 해보고 나니... 한가지 경우가 두번 리턴되는 경우를 막으려고 집합을 썼던 건데 이러면 그럴 필요가 없네...?
> 굳이 구현해보지는 않았지만, 책에서는 배열만을 이용해 문제를 풀 경우 배열의 순차탐색을 두번해야하기 때문에 시간복잡도가 무조건적으로 n^2이 되는 것을 dictionary를 이용해서 최적화한다. 이 경우 배열을 dict로 만드는건 n이지만, 탐색에는 최선 1, 최악 n의 시간복잡도를 가지게 된다. for문을 두번 써서 dictionary를 만들기도, 한번만 써서 만드는 것과 탐색을 함께 하기도 한다. 투 포인터로 푸는 방법도 나오기에 '정렬된 배열을 주지 않는데 왠 투 포인터지?' 싶었는데 아니나 다를까 실제 코딩 테스트에 이런 문제가 나왔을 때 이렇게 접근하면 안된단다... 정렬을 따로 구현하면 인덱스가 꼬여 복잡도도 늘고 코드 자체도 복잡해진다. 그리고 Go를 쓰면 속도가 압도적으로 빨라지는 것을 보여줬는데... 묘하게 설렜다. 꼭 Go랑 C++을 배워야지. C#이랑 스칼라도.

```Python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        result = set()
        
        for i1, num1 in enumerate(nums):
            for i2, num2 in enumerate(nums):
                if (num1 + num2) == target and i1 != i2:
                    result.add(i1)
                    result.add(i2)
                    continue             

        return result
```
- 결과
```
Runtime: 668 ms, faster than 5.08% of Python online submissions for Two Sum.
Memory Usage: 13.7 MB, less than 12.13% of Python online submissions for Two Sum.
```


## 【[ § ](#leetcode)】 42 [[↑]](#배열-)
> **Trapping Rain Water**   
[[문제](https://leetcode.com/problems/trapping-rain-water/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 0  | X  | X  | X  |         -  |          - | [[ § 42-1 ](#-----42----1-)] |
|21-01-15| 1  | O  | O  | O  | 1 (68.68%) | 1 (73.25%) | [[ § 42-2 ](#-----42----2-)] |

### 【[ § ](#leetcode)】 [[ § 42 ](#---42-)] - 1 [[↑]](#배열-)
예시조차 통과못했지만, 어쨌거나 노력을 기록하고자 하는 것이 취지이니 그냥 한번 넣어봤다. 원래는 리미트를 배열로 해서 숫자 2개를 사용했다가, 머리아파서 그냥 변수로 했다가, 역시 숫자 2개를 쓰는 게 맞는 것 같아서 다시 배열 형태로 바꾸려다 위에서 언급했듯 상태도 안좋고 해서 그냥 책을 봤는데, 또 투 포인터 어쩌구 하더라. 리미트를 2개 쓰려고 한 게, 비록 의도하지는 않았지만 투 포인터 방식에 가까웠던 것 같다.
> 책에서 쓴 투포인터 방식은 내가 생각한 방식과는 달랐다. 나는 왼쪽에서부터 오른쪽으로 가면서, 튀어나온 부분을 기록했다가 그 기록한 숫자가 2개가 되면 그 사이를 메꾸는 방식으로 썼는데, 이렇게 되면 3, 2, 1, 2, 같은 부분에서 3이 한쪽 튀어나온 부분을 맡고는 그 뒤로 튀어나온 부분이 없는 것으로 인식되기 때문에 문제를 해결하지 못했었는데, 책에서는 양쪽 끝에서 제일 튀어나온 기둥을 향해 오면서 결과에 바로바로 더해주더라. 양쪽 끝에서 오면서 바로바로 limit에서 높이를 빼버리니, limit가 2개가 될 때까지 기다릴 필요도 없고 뭐 그렇다.

```Python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        
        result=[0 for x in range(len(height))]
        limit = 0
        index = 0

        for i in range(len(height)):  
            if limit != 0 and height[i] >= limit:
                for n in range(index, i):
                    result[n] = min(limit, height[i]) - height[n]
                limit = height[i]
                index = i
            if limit == 0 and height[i] > limit:
                limit = height[i]
                index = i
        
        return result
```
- 결과
```
> [0, 0, 1, 0, 1, 2, 1, 0, 0, 0, 0, 0] -> 5 *정답은 6
```

### 【[ § ](#leetcode)】 [[ § 42 ](#---42-)] - 2 [[↑]](#배열-)
책에 써있는 스택으로 푸는 방법이 보는 걸로만은 이해가 안되서 한번 따라 쳐봤다. 이제 대충 무슨 느낌인지는 알겠는데, 솔직히 다른 문제가 나왔을 때 이렇게 스택으로 풀어보라고 하면 이런 식의 방법을 떠올릴 자신이 없다...

```Python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        
        stack = []
        volume = 0
        
        for i in range(len(height)):
            #변곡점을 만나면 물을 채운다.
            while stack and height[i] > height[stack[-1]]:
                #바로 직전의 height의 인덱스를 꺼낸다. 변수 이름이 top이라 제일 높은 변곡점 
                #얘기하는 줄 알고 코드 이해할 때 좀 헷갈렸는데, 스택의 꼭대기라는 의미에서 top이다.
                top = stack.pop()
                
                #근데 꺼낸 인덱스가 유일한 인덱스면 반대편 끝이 없으므로 물채우기 중지.
                if not len(stack):
                    break
            
                #현재 변곡점과 반대편 변곡점 간의 거리 가늠
                distance = i - stack[-1] -1
                #물의 높이를 양 끝의 변곡점 중 낮은 변곡점과, 현 변곡점 바로 직전 칸의 높이를 이용하여 구한다. 
                #근데 당최 정확히 어떤 원리로 물 높이가 딱 맞아지는 건지를 모르겠어서 이거 일주일지나서 구현해보라하면 못할 것 같다.
                waters = min(height[i], height[stack[-1]]) - height[top]
                
                volume += distance * waters
            
            #현재칸의 높이를 스택에 쌓는다.
            stack.append(i)
        
        return volume
```
- 결과
```
Runtime: 40 ms, faster than 68.68% of Python online submissions for Trapping Rain Water.
Memory Usage: 14.1 MB, less than 73.25% of Python online submissions for Trapping Rain Water.
```

## 【[ § ](#leetcode)】 15 [[↑]](#배열-)
> **3Sum**   
[[문제](https://leetcode.com/problems/3sum/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 3  | O  | O  | O  | 1 (75.41%)  | 1 (49.89%) | [[ § 15-1 ](#-----15----1-)] |

### 【[ § ](#leetcode)】 [[ § 15 ](#---15)] - 1 [[↑]](#배열-)
처음에 브루트 포스로 접근해서 예시는 통과했으나 실제에서 중복값이 나왔고, 어떻게 해결해보려다 포기하고 책을 봤는데, 막상 브루트 포스로 접근해서 중복값 제거까지 해놓으면 타임아웃이 일어난다더라. 결국 여기서도 투포인터를 써서 해결한다.

```Python
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        
        result = []
        #투 포인터 풀이를 위해 정렬
        #정렬하고나면 작은 값은 왼쪽에, 큰 값은 오른쪽에 위치하게 된다.
        nums.sort()
        
        
        for i in range(len(nums)-1):
            if i > 0 and nums[i] == nums[i-1]:
                #현재 값이 이전 값과 동일하면 스킵
                continue
            #i + 1 번째와 배열의 끝을 각각 포인터로 지정
            left, right = i + 1, len(nums) - 1
            while left < right:
                sum = nums[i] + nums[left] + nums[right]
                if sum < 0:
                    #합계가 0보다 작으면 값을 키우기 위해 왼쪽 포인터를 오른쪽으로 한칸
                    left += 1
                elif sum > 0:
                    #0보다 크면 값을 줄이기 위해 오른쪽 포인터를 왼쪽으로 한칸
                    right -= 1
                else:
                    #둘 다 아니면 result로 보냄
                    result.append([nums[i],nums[left],nums[right]])

                    #중복값 제거를 위한 포인터 스킵
                    while left < right and nums[left] == nums[left + 1]:
                        left += 1
                    while left < right and nums[right] == nums[right - 1]:
                        right -= 1
                    #위에서 중복값 제거를 위해 스킵할 때는 이전값과 비교했지만,
                    #여기서는 다음값과 비교하기 때문에 한칸 더 가줘야 중복값 제거가 된다.
                    left += 1
                    right -= 1
        return result 
```
- 결과
```
Runtime: 684 ms, faster than 75.41% of Python online submissions for 3Sum.
Memory Usage: 16.8 MB, less than 49.89% of Python online submissions for 3Sum.
```

# 연결 리스트 [[↑]](#--연결-리스트-)

## 【[ § ](#leetcode)】 234 [[↑]](#연결-리스트-)
> **Palindrome Linked List**   
[[문제](https://leetcode.com/problems/palindrome-linked-list/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-17| 4  | X  | O  | O  | 2 (77.18%)  | 2 (14.49%) | [[ § 234-1 ](#-----234----1-)] |
|21-01-18| 5  | O  | O  | O  | 1 (89.66%)  | 1 (97.00%) | [[ § 234-2 ](#-----234----2-)] |

### 【[ § ](#leetcode)】 [[ § 234 ](#---234-)] - 1 [[↑]](#연결-리스트-)
처음에 당연히 빈 배열은 false일꺼라 생각했는데 true여서 틀렸고, 그 다음엔 막연하게 길이가 1이거나 홀수이면 펠린드롬이 아니라고 생각했다가 틀렸다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        nodes = []
        
        if head:
            node = head
        else:
            return True
        
        while True:
            nodes.append(node.val)
            if node.next:
                node = node.next
            else:
                break
        
        if len(nodes) == 1:
            return True
        
        for i in range((len(nodes) / 2)):
            if not(nodes[i] == nodes[-(i+1)]):
                return False
            
        return True      
```
- 결과
```
Runtime: 68 ms, faster than 77.18% of Python online submissions for Palindrome Linked List.
Memory Usage: 32.9 MB, less than 14.49% of Python online submissions for Palindrome Linked List.
```

### 【[ § ](#leetcode)】 [[ § 234 ](#---234-)] - 2 [[↑]](#연결-리스트-)
이런 식으로 푸는 건 진짜 책에서 안봤으면 평생 생각도 못해봤을 것이다... 알고리즘의 세계란 참 놀랍다. 중간에 주석 친 거는 책을 안보고 기억에 의존해서 저렇게 적었었는데, 저러니 예시조차도 통과 못했었다. 그래서 나중에 저렇게 적은거랑 책에 적은거랑 어떤 식으로 다르게 동작하는 건지 살펴보려고 냅뒀다. 그리고 책에 다중 할당 어쩌고 하는 내용이 있던데 이것도 뭔소린지 잘... 나중에 다시 살펴봐야겠다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        
        rev = None
        fast = slow = head
        
        while fast and fast.next:
            fast = fast.next.next
            rev, rev.next, slow = slow, rev, slow.next
        if fast:
            slow = slow.next
            
        # while slow.next:
        #     if rev != slow:
        #         return False
        #     rev = rev.next
        #     slow = slow.next
        
        while rev and rev.val == slow.val:
            rev = rev.next
            slow = slow.next
        
        return not rev
        
            
           
```
- 결과
```
Runtime: 64 ms, faster than 89.66% of Python online submissions for Palindrome Linked List.
Memory Usage: 32.2 MB, less than 97.00% of Python online submissions for Palindrome Linked List.
```

## 【[ § ](#leetcode)】 21 [[↑]](#연결-리스트-)
> **Merge Two Sorted Lists**   
[[문제](https://leetcode.com/problems/merge-two-sorted-lists/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-21| 3  | X  | O  | O  | 1 (46.64%)  | 1 (11.42%) | [[ § 21-1 ](#-----21----1-)] |
|21-01-21| 4  | O  | O  | O  | 2 (46.64%)  | 2 (11.42%) | [[ § 21-2 ](#-----21----2-)] |

### 【[ § ](#leetcode)】 [[ § 21 ](#---21-)] - 1 [[↑]](#연결-리스트-)
문제를 보는 과정에서 책을 언뜻 봤는데 재귀 어쩌고가 써있더라... 나는 재귀로 풀 생각조차 못했었는데. 알고리즘의 세계란 참 심오하다... 아, 그리고 빈배열 거르는 법이 아직도 헷갈린다. !list 이런 식으로 하는 건 줄 알았는데 그건 아니더라. 아마 이건 None을 거르는 거지 싶다. 결국 list = []으로 걸렀다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        result = []
        
        while l1:
            result.append(l1.val)
            l1 = l1.next
        
        while l2:
            result.append(l2.val)
            l2 = l2.next
        
        if result == []:
            return None
        
        result.sort()
        result.reverse()
        
        re1, re2 = None, None
        
        for i, num in enumerate(result):
            if i == 0:
                re2 = ListNode()
                re2.val = num
            if (i+1) <= len(result):
                re1 = ListNode()
                try:
                    re1.val = result[i+1]
                except:
                    re1.val = None
                re1.next = re2
            re2 = re1
        
        return re1.next
                
            
```
- 결과
```
Runtime: 28 ms, faster than 46.64% of Python online submissions for Merge Two Sorted Lists.
Memory Usage: 13.7 MB, less than 11.42% of Python online submissions for Merge Two Sorted Lists.
```

### 【[ § ](#leetcode)】 [[ § 21 ](#---21-)] - 2 [[↑]](#연결-리스트-)
이게 책에서 나온 재귀로 푸는 방법이다. 234 - 2와 마찬가지로 책을 안봤으면 이렇게도 풀 수 있다고는 결코 생각못해봤을거다. 코드도 간결하고 좋은데, 책에 적혀있는 말마따나 너무 함축돼서 이해가 힘들다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        if (not l1) or (l2 and l1.val > l2.val):
            l1, l2 = l2, l1
        if l1:
            l1.next = self.mergeTwoLists(l1.next, l2)
        return l1       
```
- 결과
```
Runtime: 28 ms, faster than 46.64% of Python online submissions for Merge Two Sorted Lists.
Memory Usage: 13.6 MB, less than 11.42% of Python online submissions for Merge Two Sorted Lists.
```


## 【[ § ](#leetcode)】 206 [[↑]](#연결-리스트-)
> **Reverse Linked List**   
[[문제](https://leetcode.com/problems/merge-two-sorted-lists/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-21| 3  | X  | O  | O  | 1 (74.79%)  | 1 (26.44%) | [[ § 206-1 ](#-----206----1-)] |
|21-01-21| 4  | O  | O  | O  | err  | err | [[ § 206-2 ](#-----206----2-)] |

### 【[ § ](#leetcode)】 [[ § 206 ](#---206-)] - 1 [[↑]](#연결-리스트-)
21번 문제를 풀 때 썼던 방법을 응용했다. 아, !obj 같은 문법은 원래 파이썬에 없는 모양이다. 그냥 not obj로 적었는데, 그럼 !obj 문법은 도대체 어디서 봤던거지...?

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head:
            return None
        
        node = head
        
        re1, re2 = None, ListNode()
        
        while node:
            re2.val = node.val
            if node.next:
                re1 = ListNode()
                re1.next = re2      
                re2 = re1
            node = node.next
        
        return re2         
```
- 결과
```
Runtime: 24 ms, faster than 74.79% of Python online submissions for Reverse Linked List.
Memory Usage: 16.8 MB, less than 26.44% of Python online submissions for Reverse Linked List.
```

### 【[ § ](#leetcode)】 [[ § 206 ](#---206-)] - 2 [[↑]](#연결-리스트-)
방향성은 비슷한 것 같은데, 책에서 나온 방법을 쓰면 늘 코드도 간결하면서 성능도 좋다... 라고 생각해서 방법이 비슷함에도 적었는데, 방금 제출 여러번 해봤더니 숫자가 계속 바뀐다. 네트워크 문제인지, 리트코드 문제인지 뭔지 모르겠지만 결과에 너무 연연하지 말아야겠다.
책에 재귀로 하는 방법도 있었는데, 그냥 안적었다.

> 근데 설명을 읽어보다 보니까, 방향성이 '비슷'할 뿐 완전히 다른 풀이인 것 같다. 나는 새로운 객체를 만들어서 리턴했지만, 이 방법은 기존의 연결리스트를 그대로 이용한다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        node, prev = head, None
        
        while node:
            next, node.next = node.next, prev
            prev, node = node, next
            
        return prev
```
- 결과
```
err
```

## 【[ § ](#leetcode)】 2 [[↑]](#연결-리스트-)
> **Add Two Numbers**   
[[문제](https://leetcode.com/problems/add-two-numbers/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-22| 4  | X  | O  | O  | 2 (47.74%)  | 1 (46.94%) | [[ § 2-1 ](#-----2----1-)] |
|21-01-22| 5  | O  | O  | O  | 1 (67.10%)  | 2 (18.91%) | [[ § 2-2 ](#-----2----2-)] |

### 【[ § ](#leetcode)】 [[ § 2 ](#---2-)] - 1 [[↑]](#연결-리스트-)
처음에는 각 숫자를 다 더하는 줄 알았어서 아예 다르게 짰었고, 그 와중에도 0이 리턴되는 등 에러가 났었다. 그 다음에는 뒤집힌 리스트인 줄 몰랐어서 틀렸고 등등등...
> 책에서도 비슷한 방법을 사용하는데, 다른 부분은 연결 리스트를 리스트로 바꾸는 함수, 그리고 리스트를 다시 연결리스트로 바꾸는 함수를 따로 구현했다는 점, 그리고 리스트에는 숫자로 넣고, 문자열로 바꿀 때 ''.join(map(str, list)) 이런 식으로 바꾼 다는 점 등이다. 더 나아가서 아예 리스트를 바로 숫자로 바꾸는 방식도 쓰는데, 이건 다음에 공부하기로ㅎㅎ

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        num1 = []
        num2 = []
        
        while l1:
            num1.append(str(l1.val))
            l1 = l1.next
            
        while l2:
            num2.append(str(l2.val))
            l2 = l2.next
            
        num1 = int("".join(num1[::-1]))
        num2 = int("".join(num2[::-1]))
        renum = str(num1 + num2)
        
        re1, re2 = None, ListNode()
        
        for i, nu in enumerate(renum):
            re2.val = int(nu)
            re1 = ListNode()
            re1.next = re2
            re2 = re1
            
        return re1.next
                   
```
- 결과
```
Runtime: 64 ms, faster than 47.74% of Python online submissions for Add Two Numbers.
Memory Usage: 13.5 MB, less than 46.94% of Python online submissions for Add Two Numbers.
```

### 【[ § ](#leetcode)】 [[ § 2 ](#---2-)] - 2 [[↑]](#연결-리스트-)
늘상 하는 말이지만, 비슷해 보이는 방식도 책에서는 항상 더 깔끔하고 성능이 좋다...만 비슷한 방식은 이제는 뭔가 특별한 부분이 따로 있지 않으면 굳이 적지 않기로 했고, 늘상 하는 말이지만 책을 보지 않았으면 결코 생각지 못했을 방법이 늘상 나타난다. 전가산기라니...? 그런건 처음 듣는다. 아, 그리고 연결 리스트 문제를 풀 때마다 어떻게 하면 제일 처음 노드를 보존하기 수월할까 했는데, 여기서는 연달아 할당함으로써 이를 해결한다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        root = head = ListNode(0)
        
        carry = 0
        
        while l1 or l2 or carry:
            sum = 0
            
            if l1:
                sum += l1.val
                l1 = l1.next
            
            if l2:
                sum += l2.val
                l2 = l2.next
                
            carry, val = divmod(sum + carry, 10)
            head.next = ListNode(val)
            head = head.next
        
        return root.next
```
- 결과
```
Runtime: 60 ms, faster than 67.10% of Python online submissions for Add Two Numbers.
Memory Usage: 13.7 MB, less than 18.91% of Python online submissions for Add Two Numbers.
```

## 【[ § ](#leetcode)】 24 [[↑]](#연결-리스트-)
> **Swap Nodes in Pairs**   
[[문제](https://leetcode.com/problems/swap-nodes-in-pairs/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-22| 1  | X  | O  | O  | 1 (86.06%)  | 3 (9.14%) | [[ § 24-1 ](#-----24----1-)] |
|21-01-22| 2  | O  | O  | O  | 2 (60.11%)  | 2 (29.31%) | [[ § 24-2 ](#-----24----2-)] |
|21-01-22| 3  | O  | O  | O  | 2 (60.11%)  | 1 (83.54%) | [[ § 24-3 ](#-----24----3-)] |

### 【[ § ](#leetcode)】 [[ § 24 ](#---24-)] - 1 [[↑]](#연결-리스트-)
오... 예시도 안거치고 한번에!
> 책에서는 i값을 사용하는 대신 node = node.next.next를 해버림으로써 또 다시 내 풀이 보다 간결하게 풀이한다... 이 방법은 그리 좋은 풀이법이 아니라는 말과 함께... 심지어는 면접관이 이렇게 풀지 말라고 하기도 한다고 한다...

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        node = head
        i = 1
        
        while node:
            if i % 2 != 0 and node.next:
                temp = node.val
                node.val = node.next.val
                node.next.val = temp
            
            node = node.next
            i += 1
            
        return head           
```
- 결과
```
Runtime: 16 ms, faster than 86.06% of Python online submissions for Swap Nodes in Pairs.
Memory Usage: 13.7 MB, less than 9.14% of Python online submissions for Swap Nodes in Pairs.
```

### 【[ § ](#leetcode)】 [[ § 24 ](#---24-)] - 2 [[↑]](#연결-리스트-)
여기서는 값만 바꾸는 게 아니라 노드의 구조 자체를 바꾼다. 주석으로 흐름을 풀이해보면 보다 이해가 잘될 것 같아 그래보기로 했다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        root = prev = ListNode() # root, prev 설정
        
        prev.next = head # root.next = head
        
        # 예시는 현재 노드가 3이라는 전제
        while head and head.next:
            # b에 현재 노드의 다음 노드를 담는다.
            # ex. [1, 2(= prev), 3(= head), 4(= head.next), 5, 6]
            # [1,2] → [3] → [4](= b) → [5,6]
            b = head.next

            # 다음 노드의 다음 노드가 
            # 현재 노드의 다음 노드가 되도록 한다.
            # ex. [1,2] → [ 3 ] → [5,6]
            #             [ 4 ] ↗
            head.next = b.next

            # b(= 원래의 다음 노드)의 다음 노드가
            # 현재 노드가 되도록 한다.
            # ex. [1,2] ↘
            #     [ 4 ] → [ 3 ] → [5,6]            
            b.next = head
            
            # 이전 노드의 다음 노드는 b가 되면서,
            # 구조의 순서가 완전히 바뀐다.
            # ex. [1,2] → [4] → [3] → [5,6]
            prev.next = b
            
            # head와 prev의 이동
            # ex. [1, 2(= prev), 4, 3(= head), 5, 6]
            #                  p→ p→↑        h→↑
            #  => [1, 2, 4, 3(= prev), 5(= head), 6]
            head = head.next
            prev = prev.next.next
            
        return root.next
```
- 결과
```
Runtime: 16 ms, faster than 86.06% of Python online submissions for Swap Nodes in Pairs.
Memory Usage: 13.4 MB, less than 59.09% of Python online submissions for Swap Nodes in Pairs.
```


### 【[ § ](#leetcode)】 [[ § 24 ](#---24-)] - 3 [[↑]](#연결-리스트-)
책에서 나온 재귀를 통해 푸는 방법인데, 개인적으로 재귀를 좋아하지 않는다. 흐름이 연상이 잘 안되기 때문이다. 이해하지 못했으면서 코드를 쓰는 건 무용하다고 느껴서 원래는 따로 안적으려고 했는데, 코드가 워낙 이쁘기에 이것도 주석으로 풀이해보기로 했다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # [1, 2, 3, 4, 5, 6]
        # {}는 몇번째 재귀인지를 표시한 것이고,
        # 아래에 적힌 번호 순서대로 코드가 흐른다.
        
        # - 함수 시작
        # {0} 1. [1(= head), 2, 3, 4, 5, 6]
        # {1} 3. [3(= head), 4, 5, 6]
        # {2} 5. [5(= head), 6]
        # {3} 7. [] => head = None ↓↓ 8번
        if head and head.next:
            # {0} 2. [1, 2(= p), 3, 4, 5, 6]
            # {1} 4. [3, 4(= p), 5, 6]
            # {2} 6. [5, 6(= p)]
            p = head.next

            # - 재귀 구간
            # {0} 3. [1] -> swapPairs([3,4,5,6]) ↑ {1} 함수 시작 - 3번
            # {0} 15. [1] -> [4,3,6,5]
            #----------------------------------------------------------
            # {1} 5. [3] -> swapPairs([5,6]) ↑ {2} 함수 시작 - 5번
            # {1} 12. [3] -> [6,5]
            #----------------------------------------------------------
            # {2} 7. [5] -> swapPairs([]) ↑ {3} 함수 시작 - 7번
            # {2} 9. [5] -> None
            head.next = self.swapPairs(p.next)

            # {0} 16. [2] -> [1] -> [4,3,6,5]
            # {1} 13. [4] -> [3] -> [6,5]
            # {2} 10. [6] -> [5]
            p.next = head

            # {0} 17. [2,1,4,3,6,5]를 리턴
            # {1} 14. [4,3,6,5]를 리턴 ↑ {0} 재귀 구간 - 15번
            # {2} 11. [6,5]을 리턴 ↑ {1} 재귀 구간 - 12번
            return p
        
        # {3} 8. None을 리턴 ↑ {2} 재귀 구간 - 9번
        return head
```
- 결과
```
Runtime: 20 ms, faster than 60.11% of Python online submissions for Swap Nodes in Pairs.
Memory Usage: 13.4 MB, less than 83.54% of Python online submissions for Swap Nodes in Pairs.
```

## 【[ § ](#leetcode)】 328 [[↑]](#연결-리스트-)
> **Odd Even Linked List**   
[[문제](https://leetcode.com/problems/odd-even-linked-list/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-22| 3  | X  | O  | O  | 1 (89.11%)  | 1 (86.53%) | [[ § 328-1 ](#-----328----1-)] |

### 【[ § ](#leetcode)】 [[ § 328 ](#---328-)] - 1 [[↑]](#연결-리스트-)
처음엔 odd랑 even의 루트를 잃어버려서 둘을 못붙였다가, 기껏 붙여놨더니 홀수 노드로 끝나면 짝수 노드가 None으로 끝나 even_head.next에 런타임 에러가 떠서 이를 거르기 위해 조건문을 추가했다. 풀면서 왠지 재귀로 하면 더 깔끔하게 할 수 있을 것 같고, 재귀랑 별개로 굳이 head is None이나 head.next 없이 빈 노드를 자연스레 거를 수 있는 방법이 있을 것 같다는 느낌이 왔다. 책에 방법이 써있겠지?
> head is None은 어쩔 수 없는 것인지 책에도 써있지만, 빈 노드를 거르는 방법은 따로 있긴 했다. 그냥 반복문의 조건을 짝수로 하면 되는 거였다. 생각해보면 조건을 짝수로 넣으면 1개 짜리도 거를 수 있고, 홀수로 끝나도 even이 None이라 알아서 반복문이 종료될 것이며, 짝수로 끝나도 even.next가 없어 반복문이 종료될 것이기에 odd가 None이 되지도 않을텐데 미처 생각을 못했다... 그나저나 재귀로 하는 방법은 따로 안적혀있더라. 재귀로는 못하는건가? 근데 반복문으로 할 수 있는거면 분명 재귀로도 할 수 있을 것이리라. 다음에 한번 시도해봐야겠다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def oddEvenList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        if head is None:
            return head
        
        root = odd_head = head
        even_root = even_head = head.next
        
        while odd_head and odd_head.next:
            odd_head.next = odd_head.next.next
            if even_head.next:
                even_head.next = even_head.next.next
            if odd_head.next:
                odd_head = odd_head.next
            even_head = even_head.next
            
        odd_head.next = even_root
        
        return root         
```
- 결과
```
Runtime: 28 ms, faster than 89.11% of Python online submissions for Odd Even Linked List.
Memory Usage: 16.9 MB, less than 86.53% of Python online submissions for Odd Even Linked List.
```

## 【[ § ](#leetcode)】 92 [[↑]](#연결-리스트-)
> **Reverse Linked List II**   
[[문제](https://leetcode.com/problems/reverse-linked-list-ii/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-22| 3  | O  | O  | O  | 1 (66.56%)  | 1 (7.69%) | [[ § 92-1 ](#-----92----1-)] |

### 【[ § ](#leetcode)】 [[ § 92 ](#---92-)] - 1 [[↑]](#연결-리스트-)
처음에 한번에 풀라고 해서 while문에 i로 숫자 세게 해놓고 m번째부터 n번째까지 하나씩 뒤집으면서 가려고 했는데, 자꾸 시간제한을 넘겨서 맞는 지 틀린 지 조차 확인할 수가 없었다. 근데 걸린 시간을 생각해보면 아마 내가 뭘 잘못해서 while문이 안끝났던 것 같다. 막상 책을 보니 따로 노드를 지정해서 하더라마는... 근데 솔직히 노드를 따로 지정하는 방향으로 생각했더라도 책 안봤으면 이런 방법은 생각지도 못했을 것이다.

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseBetween(self, head, m, n):
        """
        :type head: ListNode
        :type m: int
        :type n: int
        :rtype: ListNode
        """
        
        if not head or m == n:
            return head
        
        root = start = ListNode()
        root.next = head
        
        # Input: 1->2->3->4->5->NULL, m = 2, n = 4
        
        for _ in range(m-1):
            start = start.next # start = 1
        end = start.next # end = 2
        
        for _ in range (n - m):
            # tmp = 2, 1 -> 3, 2 -> 4
            tmp, start.next, end.next = start.next, end.next, end.next.next
            start.next.next = tmp # 1 -> 3 -> 2(-> 4 -> 5)
            # tmp = 3, 1 -> 4, 2 -> 5
            # 1 -> 4 -> 3(-> 2 -> 5)
        
        return root.next      
```
- 결과
```
Runtime: 20 ms, faster than 66.56% of Python online submissions for Reverse Linked List II.
Memory Usage: 14 MB, less than 7.69% of Python online submissions for Reverse Linked List II.
```

# 스택, 큐 [[↑]](#--스택-큐-)

## 【[ § ](#leetcode)】 20 [[↑]](#스택-큐-)
> **Valid Parentheses**   
[[문제](https://leetcode.com/problems/valid-parentheses/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-28| 5  | O  | O  | O  | 1 (10.92%)  | 1 (98.68%) | [[ § 20-1 ](#-----20----1-)] |

### 【[ § ](#leetcode)】 [[ § 20 ](#---20-)] - 1 [[↑]](#스택-큐-)
매우 쉬우면서도 기본기를 점검할 수 있는 문제랬는데, 난 5번을 틀리고도 결국 책을 보고서야 풀었으니 난 기본이 안되어 있는 모양이다... 책을 보고도, 스택에 꽂혀서 반복문이 오른쪽에서 왼쪽으로 간다고 생각한 탓에 한동안 이게 왜 되는 건지를 이해를 못했다.

```Python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        
        if len(s) < 2:
            return False
        
        stack =[]
        con = []
        ch = 0
        
        table = {
            "}":"{",
            ")":"(",
            "]":"[",
        }
        
        for c in s:
            if c not in table:
                stack.append(c)
            elif not stack or table[c] != stack.pop():
                return False
        return len(stack) == 0   
```
- 결과
```
Runtime: 40 ms, faster than 10.92% of Python online submissions for Valid Parentheses.
Memory Usage: 13.3 MB, less than 98.68% of Python online submissions for Valid Parentheses.
```

## 【[ § ](#leetcode)】 316 [[↑]](#스택-큐-)
> **Valid Parentheses**   
[[문제](https://leetcode.com/problems/remove-duplicate-letters/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-28| 2  | O  | O  | O  | 1 (13.19%)  | 1 (25.00%) | [[ § 316-1 ](#-----316----1-)] |

### 【[ § ](#leetcode)】 [[ § 316 ](#---316-)] - 1 [[↑]](#스택-큐-)
참... 이런 걸 도대체 어떻게 생각해내지? 처음에 문제를 제대로 이해못하고 풀었을 때는 이게 왜 별 3개지 싶었는데, 문제를 이해하니까 풀기도 싫고 풀이를 봐봤자 이해도 못할 것 같아서 풀이도 보기 싫어졌었다. 뭐... 막상보니 어떤 식으로 풀리는 건 지 이해는 되는데, 이런 식으로 푸는 다른 문제를 맞딱뜨렸을 때 풀 수 있겠냐고 한다면 글쎄...

```Python
class Solution(object):
    def removeDuplicateLetters(self, s):
        """
        :type s: str
        :rtype: str
        """
        for char in sorted(set(s)):
            suffix = s[s.index(char):]
            if set(s) == set(suffix):
                return char + self.removeDuplicateLetters(suffix.replace(char,''))
        return ''
```
- 결과
```
Runtime: 68 ms, faster than 13.19% of Python online submissions for Remove Duplicate Letters.
Memory Usage: 13.9 MB, less than 25.00% of Python online submissions for Remove Duplicate Letters.
```

# 데크, 우선순위 큐 [[↑]](#--데크-우선순위-큐-)

# 해시 테이블 [[↑]](#--해시-테이블-)

## 【[ § ](#leetcode)】 771 [[↑]](#해시-테이블-)
> **Jewels and Stones**   
[[문제](https://leetcode.com/problems/remove-duplicate-letters/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-29| 1  | X  | O  | O  | 1 (57.09%)  | 1 (61.26%) | [[ § 771-1 ](#-----771----1-)] |

### 【[ § ](#leetcode)】 [[ § 771 ](#---771-)] - 1 [[↑]](#해시-테이블-)
책에 나온 풀이보다 더 간결하게 풀었다고 좋아했는데, 해시 테이블과는 상관없다고는 하나 '파이썬다운 방식'이라며 아예 1줄 짜리 풀이를 소개하더라...

```Python
class Solution(object):
    def numJewelsInStones(self, jewels, stones):
        """
        :type jewels: str
        :type stones: str
        :rtype: int
        """
        table = defaultdict(int)
        for j in jewels:
            table[j] = 1
            
        i = list(map(lambda x:table[x], stones))
        
        return sum(i)
```
- 결과
```
Runtime: 20 ms, faster than 57.09% of Python online submissions for Jewels and Stones.
Memory Usage: 13.5 MB, less than 61.26% of Python online submissions for Jewels and Stones.
```

## 【[ § ](#leetcode)】 347 [[↑]](#해시-테이블-)
> **Top K Frequent Elements**   
[[문제](https://leetcode.com/problems/top-k-frequent-elements/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-29| 2  | X  | O  | O  | 1 (22.85%)  | 1 (32.07%) | [[ § 347-1 ](#-----347----1-)] |

### 【[ § ](#leetcode)】 [[ § 347 ](#---347-)] - 1 [[↑]](#해시-테이블-)
책에서 왜 그렇게 해석했는 지는 모르겠는데, k번 이상 등장하는 요소를 추출하는 것이 아니라 k개까지의 자주 등장하는 요소를 추출하는 것이다. 덕분에 1번 틀렸다.
그리고 아니나 다를까 또 한줄 짜리 코드를 소개한다... 그리고 책에서 처음 카운터를 써서 풀 때, 카운터의 메서드를 쓰지 않고 굳이 자료구조를 하나 더 끌어와서 푸는데, 다른 풀이에서는 카운터의 메서드를 쓰는 걸 보면 아마 그냥 자료구조를 이용해 푸는 풀이를 보여줌으로써 자료구조에 대한 설명을 추가로 하기 위해서였던 것 같다.

```Python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        
        table = Counter(nums)
        result = []
        for pair in table.most_common(k):
            result.append(pair[0])
        
        return result
        # 한줄로는,
        # return list(zip(*collections.Counter(nums).most_common(k)))[0]
```
- 결과
```
Runtime: 108 ms, faster than 22.85% of Python online submissions for Top K Frequent Elements.
Memory Usage: 17 MB, less than 32.07% of Python online submissions for Top K Frequent Elements.
```

# 그래프 [[↑]](#--그래프-)

## 【[ § ](#leetcode)】 77 [[↑]](#그래프-)
> **Combinations**   
[[문제](https://leetcode.com/problems/combinations/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-29| 1  | O  | O  | O  | 1 (22.85%)  | 1 (32.07%) | [[ § 77-1 ](#-----77----1-)] |

### 【[ § ](#leetcode)】 [[ § 77 ](#---77-)] - 1 [[↑]](#그래프-)
이번에도 'k개의 조합을 리턴하라'라며 번역이 다소 모호하게 되어있다. 다만 이번에는 아예 틀린 것은 아니고, 예시를 보면 어떤 뜻인지 알 수 있긴 하다. 이제 슬슬 책을 안보고는 풀려는 시도조차 하기 힘든 문제가 계속 나온다. 너무 괴념치않고 그냥 지금은 배우는 중이라 어쩔 수 없다고 생각하려하며, 책을 아예 따라한 대부분의 문제들은 나중에 직접 풀어보고 추가하고자 따로 추가하지 않았다. 알고리즘을 이용하되 k-1을 재귀 호출함으로써 모듈에 준하는 속도를 낼 수 있다고 한다는데, 어떤 방법인지 짐작도 안간다. 책에서도 직관적인 이해가 힘들어 굳이 그 방법은 쓰지 않았다고 한다. 나중에 도전해보면 좋겠다.

```Python
class Solution(object):
    def combine(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[List[int]]
        """
        results = []
        
        # elements = 탐색 루트
        # start = 탐색 시작 지점
        # k = 탐색 거리
        def dfs(elements, start, k):
            # 남은 탐색 거리가 0이 되면,
            # 지금까지 거쳐온 탐색 루트를 결과에 추가
            if k == 0:
                results.append(elements[:])
            
            # 탐색 시작 지점 ~ n 사이의 i에 대해,
            # start와 n+1이 같아지면 그냥 스킵되는 듯?
            for i in range(start, n+1):
                # i를 탐색 루트에 추가
                elements.append(i)
                # 재귀(탐색 루트, 탐색 시작 지점 + 1, 탐색 거리 - 1)
                dfs(elements, i+1, k-1)
                # 재귀로부터 빠져나오면서 탐색 루트도 다시 한칸 뒤로
                elements.pop()
        
        dfs([], 1, k)
        
        return results
        
        # return list(map(list,itertools.combinations(range(1, n+1),k)))
        # itertools는 만능?
```
- 결과
```
Runtime: 560 ms, faster than 71.15% of Python online submissions for Combinations.
Memory Usage: 15.1 MB, less than 29.20% of Python online submissions for Combinations.
```

## 【[ § ](#leetcode)】 39 [[↑]](#그래프-)
> **Combination Sum**   
[[문제](https://leetcode.com/problems/combination-sum/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-29| 1 -> 2 | X  | O  | X -> O  | 1(5.05) | 1(41.25) | [[ § 39-1 ](#-----39----1-)] |

### 【[ § ](#leetcode)】 [[ § 39 ](#---39-)] - 1 [[↑]](#그래프-)
그래프 문제 중 처음으로 혼자 푸는 것에 도전해서 예시나마 통과한 풀이이기에 추가해봤다. 정답도, 아웃풋도 수가 너무 많아서 정확히 어떻게 틀린 것인지 판별이 안됐는데, 일단 아웃풋의 수가 정답의 수보다 월등히 많다. 혹시 target과 일치하지 않는 루트도 들어갔나 싶어 제거하는 코드를 추가해봤는데도 여전히 많아, 모종의 이유로 중복값이 들어간건가 싶어 보니 아니나 다를까 바로 첫줄에 중복값이 있더라. 근데 왜 들어갔지...?
> 내가 빡대가리였다. 중간에 탐색 루트를 정렬한 후, 중복을 방지하기 위해  결과에 정렬된 탐색루트와 일치하는 루트가 있는 지 확인해놓고, 정작 결과에는 정렬 이전의 루트를 추가했다. 그거 고치니 바로 되더라.

```Python
class Solution(object):
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        
        results = []
        
        def dfs(vec, val):
            if val >= target:
                if val == target:
                    re = sorted(vec[:])
                    if re not in results:
                        results.append(vec[:])
                return
            
            for n in candidates:
                vec.append(n)
                dfs(vec, sum(vec))
                vec.pop()
                
        dfs([], 0)
        
        return results
```
- 결과
```
~~정답이 너무 길었다...~~

Runtime: 664 ms, faster than 5.05% of Python online submissions for Combination Sum.
Memory Usage: 13.6 MB, less than 41.25% of Python online submissions for Combinatio
n Sum.
```

## 【[ § ](#leetcode)】 207 [[↑]](#그래프-)
> **Course Schedule**   
[[문제](https://leetcode.com/problems/course-schedule/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-29| 3  | O  | O  | ?  |     -      |     -      | [[ § 207-1 ](#-----207----1-)] |
|21-01-29| 3  | O  | O  | O  |     -      |     -      | [[ § 207-2 ](#-----207----2-)] |

### 【[ § ](#leetcode)】 [[ § 207 ](#---207-)] - 1 [[↑]](#그래프-)
이유는 모르겠는데, 이렇게 하면 시간제한을 초과한다. 예시를 그대로 적은 것 같은데 왜...? 네트워크나 뭐 그런거 문제인 것 같다.
```Python
class Solution(object):
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        
        graph = defaultdict(list)
        
        for x, y in prerequisites:
            graph[x].append(y)
        
        traced = set()
        
        def dfs(i):
            # 탐색한 곳을 다시 탐색해야 하는 상황이 오면
            # False를 리턴
            if i in traced:
                return False
            
            # 현재 노드를 탐색했음을 기록
            traced.add(i)
            
            # 현재 노드가 탐색해야 하는 곳(들)인 y에 대해,
            for y in graph[i]:
                # 재귀를 했는데 한번이라도 False가 리턴됐을 경우,
                # 차례대로 올라오면서 계속 False를 리턴함으로써
                # 최종 결과도 False가 됨
                if not dfs(y):
                    return False
                
            # False가 리턴되지 않은 경우,
            # 이전 노드로 돌아오는 과정에서
            # 탐색했던 노드를 탐색 기록으로부터 삭제
            traced.remove(i)
                
            # 단 한번도 False가 없었으면 True를 리턴
            return True
        
        for x in list(graph):
            if not dfs(x):
                return False
        
        return True
```
- 결과
```
?
```

### 【[ § ](#leetcode)】 [[ § 207 ](#---207-)] - 2 [[↑]](#그래프-)
위 풀이의 가지치기 버전. 이때는 제대로 결과가 나왔다.
```Python
class Solution(object):
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        
        graph = defaultdict(list)
        
        for x, y in prerequisites:
            graph[x].append(y)
        
        traced = set()
        visited = set()
        
        def dfs(i):
            # 탐색한 곳을 다시 탐색해야 하는 상황이 오면
            # False를 리턴
            if i in traced:
                return False

            # 이미 검증이 끝난 곳이면 True를 리턴
            if i in visited:
                return True
            
            # 현재 노드를 탐색했음을 기록
            traced.add(i)
            
            # 현재 노드가 탐색해야 하는 곳(들)인 y에 대해,
            for y in graph[i]:
                # 재귀를 했는데 한번이라도 False가 리턴됐을 경우,
                # 차례대로 올라오면서 계속 False를 리턴함으로써
                # 최종 결과도 False가 됨
                if not dfs(y):
                    return False
                
            # False가 리턴되지 않은 경우,
            # 이전 노드로 돌아오는 과정에서
            # 탐색했던 노드를 탐색 기록으로부터 삭제
            traced.remove(i)

            # 검증이 끝난 노드임을 기록
            visited.add(i)
                
            # 단 한번도 False가 없었으면 True를 리턴
            return True
        
        for x in list(graph):
            if not dfs(x):
                return False
        
        return True
```
- 결과
```
?
```

# 트리 [[↑]](#--트리-)

## 【[ § ](#leetcode)】 104 [[↑]](#트리-)
> **Maximum Depth of Binary Tree**   
[[문제](https://leetcode.com/problems/maximum-depth-of-binary-tree/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-02-04| 1  | X  | O  | O  |  1 (49.85) |  1 (10.56) | [[ § 104-1 ](#-----104----1-)] |

### 【[ § ](#leetcode)】 [[ § 104 ](#---104-)] - 1 [[↑]](#그래프-)
이 문제 풀면서 알고리즘 공부한 보람이 있구나 싶었다. 내가 그토록 꺼림칙하게 여겼던 재귀를 스스로 이용해서 한번에 풀었다는게 참 감격스럽더라. 비록 굉장히 쉬운 문제였기는 하지만, 내가 지금까지 공부를 해오지 않았더라면 아마 못풀었을 것이라 생각되니 굳이 스스로 별 거 아니라고 여기기 보다는 대견하게 여기고 싶다.
> 근데 정작 책에서 소개한 너비우선탐색 방식은 생각도 못했다. 여전히 아직 많이 부족하구나.
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        node = root
        d = 1
        
        def dig(node, d):
            if node.left or node.right:
                ln = dig(node.left,d) if node.left else 0
                rn = dig(node.right,d) if node.right else 0
                n = ln if ln >= rn else rn
                d += n
            return d
        
        return dig(node,d)
```
- 결과
```
Runtime: 44 ms, faster than 49.85% of Python3 online submissions for Maximum Depth of Binary Tree.
Memory Usage: 16.4 MB, less than 10.56% of Python3 online submissions for Maximum Depth of Binary Tree.
```

## 【[ § ](#leetcode)】 543 [[↑]](#트리-)
> **Diameter of Binary Tree**   
[[문제](https://leetcode.com/problems/longest-univalue-path/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-02-04| 1  | O  | O  | O  |  1 (19.20) |  1 (62.98) | [[ § 543-1 ](#-----543----1-)] |

### 【[ § ](#leetcode)】 [[ § 543 ](#---543-)] - 1 [[↑]](#그래프-)
참... 낫 놓고 기역자도 모른다고... 왠지 위의 문제에서 쓴 방식을 응용하면 될 것 같다고는 생각은 하고 있었지만 생각하려니 머리 아파서 책을 봤는데, 응용까지 갈 것도 없이 코드를 조금만 바꾸면 되는 거 였다. 돌이켜보면, 위에서 깊이우선탐색을 사용함으로써 굳이 리소스를 낭비했으면서, 정작 깊이우선탐색이 필요했던 이 문제는 스스로 해결을 못한 셈이니, 참으로 통탄스러운 바가 아닐 수 없다.
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    longest = 0
    def diameterOfBinaryTree(self, root: TreeNode) -> int:
        def dig(node):
            if not node:
                return -1
            ln = dig(node.left)
            rn = dig(node.right)
            self.longest = max(self.longest, ln+rn+2)
            return max(ln,rn)+1
            
            
        dig(root)
        return self.longest
```
- 결과
```
Runtime: 60 ms, faster than 19.20% of Python3 online submissions for Diameter of Binary Tree.
Memory Usage: 16.3 MB, less than 62.98% of Python3 online submissions for Diameter of Binary Tree.
```

## 【[ § ](#leetcode)】 687 [[↑]](#트리-)
> **Longest Univalue Path**   
[[문제](https://leetcode.com/problems/diameter-of-binary-tree/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-02-04| 6  | O  | O  | O  |  1 (80.02) |  1 (52.46) | [[ § 687-1 ](#-----687----1-)] |

### 【[ § ](#leetcode)】 [[ § 687 ](#---687-)] - 1 [[↑]](#그래프-)
분명 혼자 힘으로 풀 수 있을 것 같았는데, 자꾸 뭘 하나씩 틀리더라. 일직선이 아닌 경우를 놓친다던지, 전체가 값이 다 똑같아 선이 여러 갈래로 갈라져 그 모든 갈래의 길이를 합산해버린다던지... 결국 책을 봐야 했는데, 지금 상태가 안좋은 건지 뭔지 보고 따라쳐놓고 안됐을 때 혼자서 왜 안된건지 생각안해보고 바로 책 다시 들여다보게 되더라. 막상 보니 조금만 생각해보면 책을 다시 안봤어도 되는 거 였는데, 공부는 이런 식으로 하면 안된다는 생각이 퍼뜩 들었다. 내가 이해하지 못한 코드를 이런 식으로 공부하면 안된다.
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    longest = 0
    def longestUnivaluePath(self, root: TreeNode) -> int:
        def dfs(node):
            if not node:
                return 0
            
            left = dfs(node.left)
            right = dfs(node.right)
            
            if node.left and node.left.val == node.val:
                left += 1
            else:
                left = 0
            if node.right and node.right.val == node.val:
                right += 1
            else:
                right = 0
            
            self.longest = max(self.longest, left + right)
            
            return max(left, right)
        
        dfs(root)
        
        return self.longest
```
- 결과
```
Runtime: 60 ms, faster than 19.20% of Python3 online submissions for Diameter of Binary Tree.
Memory Usage: 16.3 MB, less than 62.98% of Python3 online submissions for Diameter of Binary Tree.
```

## 【[ § ](#leetcode)】 226 [[↑]](#트리-)
> **Invert Binary Tree**   
[[문제](https://leetcode.com/problems/invert-binary-tree/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-02-04| 1  | X  | O  | O  |  1 (86.14) |  1 (75.46) | [[ § 226-1 ](#-----226----1-)] |

### 【[ § ](#leetcode)】 [[ § 226 ](#---226-)] - 1 [[↑]](#그래프-)
설마 이게 되나? 했는데 단번에 됐다. 위의 문제들로 떨어져있던 자신감을 단번에 채워주었다. 근데 다른 한편으로는 이렇게 쉬운 문제에... 자신감이 채워진다는게 좀... 그런 것 같기도 하고....ㅎㅎ
> 그리고 또 어김없이 책에서는 같은 방식의 더 깔끔하고 간결하며 효율적인 풀이를 선보인다.

> 책에서 소개한 너비우선탐색은 이 방식과는 다르게 내려가면서 스왑한다. 너비우선탐색을 쓰면 큐에 자연스럽게 각 층별 노드를 차례대로 담으면서 스왑한다.

> 여기서 깊이 우선 탐색이라며 뭘 하나 더 소개한다. 너비우선탐색에서 조금 바뀐 정도인데, 깊이 우선 탐색 = 재귀 라고 생각했는데 꼭 그런 식은 아닌가 보다. 너비우선탐색에서는 자연스레 층별로 큐에 노드가 담기고 층별로 스왑이 되는 것에 반해, 깊이우선탐색은 스택을 써서 노드를 쭉 따라가 리프까지 가고 나서야 반대쪽 노드를 탐색하게 되는 식이다.

> 그외에 후위순회라면서 또 아주 조금 바뀐 풀이를 선보이는데, 아마 왼쪽부터 탐색하면 전위고 오른쪽부터 탐색하면 후위인 모양이다.
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        def dfs(node):
            if not node:
                return None
            
            node.left, node.right = dfs(node.right), dfs(node.left)
            
            return node
        
        return dfs(root)
```
- 결과
```
Runtime: 28 ms, faster than 86.14% of Python3 online submissions for Invert Binary Tree.
Memory Usage: 14.1 MB, less than 75.46% of Python3 online submissions for Invert Binary Tree.
```