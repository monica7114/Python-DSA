# How Many Numbers Are Smaller Than the Current Number
## Brute Force Approach
``` python
class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        n=len(nums)
        ans=[]
        for i in range(n):
            count=0
            for j in range(n):
                if nums[j]<nums[i]:
                    count+=1
            ans.append(count)
        return ans
```
## Optimized Approah
## Using Prefix and Frequency
```python
class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        count=[0]*101
        for num in nums:
            count[num]+=1
        for num in range(1,101):
            count[num]+=count[num-1]
        ans=[]
        for num in nums:
            if num==0:
                ans.append(0)
            else:
                ans.append(count[num-1])
        return ans
```
