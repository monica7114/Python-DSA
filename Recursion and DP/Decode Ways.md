# Decode Ways
## Using ord() Unicode
``` python
class Solution:
    def numDecodings(self, s: str) -> int:
        if not s or s[0] == '0':
            return 0

        prev2 = 1
        prev1 = 1
        n = len(s)
        
        for i in range(1, n):
            curr = 0
            c = s[i]

            # Single digit decode
            if c != '0':
                curr = prev1

            # Two-digit decode
            two = (ord(s[i-1]) - 48) * 10 + (ord(c) - 48)
            if 10 <= two <= 26:
                curr += prev2

            prev2 = prev1
            prev1 = curr

        return prev1
```
# Using DP
``` python
class Solution:
    def numDecodings(self, s: str) -> int:
        n=len(s)
        dp=[0]*(n+1)
        dp[0] = 1  # empty string has 1 valid decoding
        
        # If the first char is '0' → no valid decoding
        dp[1] = 0 if s[0] == '0' else 1
        for i in range(2,n+1):
            if s[i-1] != '0':  
                dp[i] += dp[i-1]
            two=int(s[i-2:i])
            if two>=10 and two<=26:
                dp[i]+=dp[i-2]
        return dp[n]
```
