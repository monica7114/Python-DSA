# Longest Common Prefix
``` python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        res=""
        ref=strs[0]
        n1=len(ref)
        n=len(strs)
        for i in range(n1):
            
            for s in strs[1:]:
                if i >= len(s):
                    return res
                if s[i]!=ref[i]:
                    return res
            res=res+ref[i]
        return res            
```
