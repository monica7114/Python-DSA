# Merge Intervals
``` python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals or not intervals[0]:
            return []
        if len(intervals)==1:
            return intervals
        
        intervals.sort(key=lambda x: x[0])
        res=[intervals[0]]

        for current_start, current_end in intervals[1:]:
            last_merged=res[-1][1]
            if current_start<=last_merged:
                res[-1][1]=max(last_merged,current_end)
            else:
                res.append([current_start,current_end])
                
        return res
            
```
