# Clibing Stairs
## Using Recursion
``` python
def solve(n):
    if n == 0 or n == 1:
        return 1

    return solve(n-1) + solve(n-2)
```
## Using Memoization
``` python
class Solution:
    def climbStairs(self, n: int) -> int:
        memo = {}

        def solve(x):
            if x == 0 or x == 1:
                return 1

            if x in memo:
                return memo[x]

            memo[x] = solve(x - 1) + solve(x - 2)
            return memo[x]

        return solve(n)
```
