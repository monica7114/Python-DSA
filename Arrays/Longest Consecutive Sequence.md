# Longest Consecutive Sequence
## Using Set
``` python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num1=set(nums)
        longest_steak=0
        for num in num1:
            if num-1 not in num1:
                
                current_steak=1
                while num+current_steak in num1:
                    current_steak+=1
                longest_steak=max(longest_steak,current_steak)
        return longest_steak
            



```
