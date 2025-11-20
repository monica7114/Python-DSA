# Best Time to Buy and Sell Stock
## Using sliding window
``` python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        left = 0         # buy pointer
        max_profit = 0

        for right in range(1, len(prices)):
            if prices[right] > prices[left]:
                profit = prices[right] - prices[left]
                max_profit = max(max_profit, profit)
            else:
                # reset the window because we found a smaller price
                left = right

        return max_profit
```
## Using Minimum and Maximum price
``` python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l_min=float('inf')
        n=len(prices)
        l_max=0
        
        for price in prices:
            l_min=min(l_min, price)
            l_max=max(l_max,price-l_min)
            
        return l_max
```
