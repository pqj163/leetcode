# leetcode

1. [937 - Reorder Log Files](https://github.com/pqj163/leetcode/blob/main/README.md#937---reorder-log-files%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)

## 937 - Reorder Log Files[(문제 목차)](https://github.com/pqj163/leetcode/blob/main/README.md#leetcode)[(문제)](https://leetcode.com/problems/reorder-data-in-log-files/)
[937 - (2). 1](https://github.com/pqj163/leetcode/blob/main/README.md#937--2-1-%EB%8B%B5-%EB%AA%A9%EC%B0%A8) : 시간 1등, 공간 1등

### 937 - (2). 1 [(답 목차)](https://github.com/pqj163/leetcode/blob/main/937%20-%20Reorder%20Log%20Files/README.md#937---reorder-log-files%EB%AC%B8%EC%A0%9C-%EB%AA%A9%EC%B0%A8%EB%AC%B8%EC%A0%9C)
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
