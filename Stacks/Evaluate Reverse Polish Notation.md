# Evaluate Reverse Polish Notation
``` python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        s=deque()
        for ch in tokens:
            if ch.lstrip('-').isdigit():
                s.append(int(ch))
            else:
                b = s.pop()
                a = s.pop()

                if ch == '+':
                    s.append(a + b)
                elif ch == '-':
                    s.append(a - b)
                elif ch == '*':
                    s.append(a * b)
                else:  # '/'
                    s.append(int(a / b))
        return s.pop()

```
