# Reorganize String
``` python
class Solution:
    def reorganizeString(self, s: str) -> str:
        count=collections.Counter(s)
        n=len(s)
        for char,value in count.items():
            if value > (n+1)//2:
                return ""
        max_heap=[(-value,char) for char,value in count.items()]
        heapq.heapify(max_heap)
        result=[]
        previous=(0,'')
        while max_heap :
            if max_heap:
                count,char=heapq.heappop(max_heap)
                result.append(char)
                if previous[0]<0:
                    heapq.heappush(max_heap,previous)
                count+=1
                previous=(count,char)
            else:
                return "".join(result)
        return "".join(result)
```


            

