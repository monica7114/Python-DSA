# Palindromic Substrings
``` python
class Solution:
    def countSubstrings(self, s: str) -> int:
        
        def hel(left:int,right:int):
            curr=0
            while left>=0 and right<len(s) and s[left]==s[right]:
                curr+=1
                left-=1
                right+=1
            return curr
        count=0
        for i in range(len(s)):
            count+=hel(i,i)
            count+=hel(i,i+1)
        return count
```
