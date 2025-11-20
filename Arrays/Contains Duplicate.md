# Contains Duplicate
## Using Frequency 
``` python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        freq={}
        for num in nums:
            freq[num]=freq.get(num,0)+1
            if freq[num]>=2:
                return True
        return False
```
## Using Set
``` python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False
```
