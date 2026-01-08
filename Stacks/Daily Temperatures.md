# Daily Temperatures
``` python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        n=len(temperatures)
        s=[]
        answer=[]
        for i in range(n-1,-1,-1):
            if not s:
                s.append(i)
                answer.append(0)
                
            else:
                while s and temperatures[i] >= temperatures[s[-1]]:
                    s.pop()
                if not s:
                    answer.append(0)
                    s.append(i)
                else:
                    answer.append(s[-1]-i)
                    s.append(i)
        answer.reverse()
        return answer
```
                








