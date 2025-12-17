# Build an Array With Stack Operations
``` python
class Solution:
    def buildArray(self, target: List[int], n: int) -> List[str]:
        output=[]
        j=0
        for i in range(1,n+1):
            output.append("Push")
            if i==target[j]:
                j+=1
                if j==len(target):
                    break
            else:
                output.append("Pop")
            
        return output

```
