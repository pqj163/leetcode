# leetcode

1. [937 - Reorder Data in Log Files
](https://github.com/pqj163/leetcode/blob/main/README.md#937---reorder-data-in-log-files%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)
2. [334 - Reverse String](https://github.com/pqj163/leetcode/blob/main/README.md#334---reverse-string%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)

## [●](https://github.com/pqj163/leetcode/blob/main/README.md#leetcode) 937 - Reorder Data in Log Files[(문제)](https://leetcode.com/problems/reorder-data-in-log-files/)
[2 : 1 (937)](https://github.com/pqj163/leetcode/blob/main/README.md#2--1-937-%EB%8B%B5-%EB%AA%A9%EC%B0%A8) - 1 & 1

### 2 : 1 (937) [(답 목차)](https://github.com/pqj163/leetcode/blob/main/README.md#937---reorder-log-files%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)
문자열을 리스트를 보고 쪼갠 다음 리스트의 요소로 정렬한 것 까지는 똑같았는데, 처음엔 2번째 요소로만 정렬했었다가 2번째 요소는 같은데 3번째 요소는 다른 로그가 인풋으로 들어와서 틀렸다.
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

## 334 - Reverse String[(문제 목차)](https://github.com/pqj163/leetcode/blob/main/README.md#leetcode)[(문제)](https://leetcode.com/problems/reorder-data-in-log-files/)
[1 : 1 (334)](https://github.com/pqj163/leetcode/blob/main/README.md#1--1-334-%EB%8B%B5-%EB%AA%A9%EC%B0%A8) - 1 & 1

### 1 : 1 (334) [(답 목차)](https://github.com/pqj163/leetcode/blob/main/README.md#334---reverse-string%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)
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
