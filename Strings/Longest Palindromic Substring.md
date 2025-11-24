# Longest Palindromic Substring
``` python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s)<2:
            return s
        longest_sub=""
        def hel(left:int,right:int):
            while left>=0 and right<len(s) and s[left]==s[right]:
                left-=1
                right+=1
            return s[left+1:right]
        for i in range(len(s)):
            p1=hel(i,i)
            p2=hel(i,i+1)
            if len(p1) > len(longest_sub):
                longest_sub = p1
                
            if len(p2) > len(longest_sub):
                longest_sub = p2
        return longest_sub
    
```
