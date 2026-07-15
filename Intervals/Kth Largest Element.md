# Kth Largest Element
``` python
import heapq
def KthLargest(nums, k):

        heap = []
        for num in nums:
            heapq.heappush(heap, num)
            if len(heap) >k:
                heapq.heappop(heap)
        return heap[0]
```
