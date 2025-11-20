# Fibonacci
## Using Recursion
``` python
class Solution:
    def fib(self, n: int) -> int:
        if n==0:
            return 0
        if n==1:
            return 1
        
        return self.fib(n-1)+self.fib(n-2)
```
## Using Memoization
``` python
class Solution:
    def fib(self, n: int) -> int:
        memo = {}  # step 1: dictionary to store computed results

        def solve(x):
            # step 3: base cases
            if x == 0:
                return 0
            if x == 1:
                return 1

            # step 4: if result already known
            if x in memo:
                return memo[x]

            # step 5: compute and store in memo
            memo[x] = solve(x - 1) + solve(x - 2)
            return memo[x]

        return solve(n)
```
