# Non-overlapping Intervals
``` python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        if not intervals:
            return 0
        
        interval=1
        intervals.sort(key=lambda x:x[1])
        last=intervals[0][1]
        for i in range(1,len(intervals)):
            current_start = intervals[i][0]
            current_end = intervals[i][1]
            if current_start>=last:
                interval+=1
                last=current_end
        return len(intervals)-interval


```
