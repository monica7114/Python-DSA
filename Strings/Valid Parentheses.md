# Valid Parentheses
``` python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s)%2!=0:
            return False

        st=[]
        dic={')':'(', ']':'[', '}':'{'}
        for ch in s:
            if ch in dic.values():
                st.append(ch)
            else:
                if not st:
                    return False
                if dic[ch]!=st.pop():
                    return False
        return not st

```
