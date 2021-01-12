# leetcode

[937 - Reorder Log Files](https://github.com/pqj163/leetcode/tree/main#937---reorder-log-files)

### 937 - Reorder Log Files[목차](https://github.com/pqj163/leetcode/blob/main/README.md)[문제](https://leetcode.com/problems/reorder-data-in-log-files/)
1. 두번째 시도, 첫번째 정답
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
