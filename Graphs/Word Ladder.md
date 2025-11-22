# Word Ladder
## Using BFS
``` python
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        if endWord not in wordList:
            return 0
        l=len(beginWord)
        patterns=defaultdict(list)
        for word in wordList:
            for i in range(l):
                pattern=word[:i]+"*"+word[i+1:]
                patterns[pattern].append(word)
        q=deque([(beginWord,1)])
        visited=set([beginWord])
        while q:
            word,level=q.popleft()
            l=len(word)
            for i in range(l):
                pattern=word[:i]+"*"+word[i+1:]
                for nei in patterns[pattern]:
                    if nei==endWord:
                        return level+1
                    if nei not in visited:
                        visited.add(nei)
                        q.append((nei,level+1))
                
        return 0
        

```
