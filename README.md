# leetcode

1. [937 - Reorder Data in Log Files
](#---937)
2. [344 - Reverse String](#---344)
3. [819 - Most Common Word](#---819)
4. [49 -  Group Anagrams](#---49)
5. [5 - Longest Palindromic Substring](#---5)
6. [1 - Two Sum](#---1)
7. [42 - Trapping Rain Water](#---42)
8. [15 - 3Sum](#---15)
9. [234 - Palindrome Linked List](#---234)
10. [21 - Merge Two Sorted Lists](#---21)

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

## 【[ § ](#leetcode)】 5
> **Longest Palindromic Substring**   
[[문제](https://leetcode.com/problems/longest-palindromic-substring/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-13| 9  | O  | O  | O  | 1 (94.42%)  | 1 (76.37%) | [[ § 5-1 ](#-----5----1)] |

### 【[ § ](#leetcode)】 [[ § 5 ](#---5)] - 1 
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


## 【[ § ](#leetcode)】 1
> **Two Sum**   
[[문제](https://leetcode.com/problems/two-sum/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 5  | X  | O  | O  | 1 (5.08%)  | 1 (12.13%) | [[ § 1-1 ](#-----1----1)] |

### 【[ § ](#leetcode)】 [[ § 1 ](#---1)] - 1 
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


## 【[ § ](#leetcode)】 42
> **Trapping Rain Water**   
[[문제](https://leetcode.com/problems/trapping-rain-water/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 0  | X  | X  | X  |         -  |          - | [[ § 42-1 ](#-----42----1)] |
|21-01-15| 1  | O  | O  | O  | 1 (68.68%) | 1 (73.25%) | [[ § 42-2 ](#-----42----2)] |

### 【[ § ](#leetcode)】 [[ § 42 ](#---42)] - 1 
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

### 【[ § ](#leetcode)】 [[ § 42 ](#---42)] - 2 
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

## 【[ § ](#leetcode)】 15
> **3Sum**   
[[문제](https://leetcode.com/problems/3sum/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-15| 3  | O  | O  | O  | 1 (75.41%)  | 1 (49.89%) | [[ § 15-1 ](#-----15----1)] |

### 【[ § ](#leetcode)】 [[ § 15 ](#---15)] - 1 
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


## 【[ § ](#leetcode)】 234
> **Palindrome Linked List**   
[[문제](https://leetcode.com/problems/palindrome-linked-list/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-17| 4  | X  | O  | O  | 2 (77.18%)  | 2 (14.49%) | [[ § 234-1 ](#-----234----1)] |
|21-01-18| 5  | O  | O  | O  | 1 (89.66%)  | 1 (97.00%) | [[ § 234-2 ](#-----234----2)] |

### 【[ § ](#leetcode)】 [[ § 234 ](#---234)] - 1 
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

### 【[ § ](#leetcode)】 [[ § 234 ](#---234)] - 2 
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

## 【[ § ](#leetcode)】 21
> **Merge Two Sorted Lists**   
[[문제](https://leetcode.com/problems/merge-two-sorted-lists/)] 

|  일자  |시도|참고|예시|정답|     시간    |     공간   | § | 
|:------:|:--:|:--:|:--:|:--:|:----------:|:----------:|:--:|
|21-01-21| 3  | X  | O  | O  | 1 (46.64%)  | 1 (11.42%) | [[ § 21-1 ](#-----21----1)] |
|21-01-21| 4  | O  | O  | O  | 1 (19.93%)  | 1 (11.42%) | [[ § 21-2 ](#-----21----2)] |

### 【[ § ](#leetcode)】 [[ § 21 ](#---21)] - 1 
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

### 【[ § ](#leetcode)】 [[ § 21 ](#---21)] - 2 
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
Runtime: 64 ms, faster than 89.66% of Python online submissions for Palindrome Linked List.
Memory Usage: 32.2 MB, less than 97.00% of Python online submissions for Palindrome Linked List.
```