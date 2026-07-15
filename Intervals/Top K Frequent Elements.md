# Top K Frequent Elements
``` python
from collections import Counter
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count=Counter(nums)
        heap=[]
        for num,cnt in count.items():
            heapq.heappush(heap,(cnt,num))
            if len(heap)>k:
                heapq.heappop(heap)
        return [num for freq,num in heap]
```
