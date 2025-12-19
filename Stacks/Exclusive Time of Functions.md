#  Exclusive Time of Functions
``` python
class Solution:
    def exclusiveTime(self, n: int, logs: List[str]) -> List[int]:
        stack=[]
        ans=[0]*n
        prev=0
        for log in logs:
            fn,ty, time= log.split(":")
            fn,time=int(fn),int(time)
            if ty=="start":
                if stack:
                    ans[stack[-1]]+= time-prev
                stack.append(fn)
                prev=time
            else:
                ans[stack.pop()]+= time-prev+1
                prev=time+1
        return ans
```
