# Design Add and Search Words Data Structure
``` python
class Trie:
    def __init__(self):
        self.children={}
        self.is_end=False
class WordDictionary:

    def __init__(self):
        self.root=Trie()
        

    def addWord(self, word: str) -> None:
        node=self.root
        for ch in word:
            
            if ch not in node.children:
                node.children[ch]=Trie()
            node=node.children[ch]
        node.is_end=True


    def search(self, word: str) -> bool:
        node=self.root
        def dfs(node,i):

            for ch in word:
                if i==len(word):
                    return node.is_end
                ch=word[i]
                if ch=='.':
                    return any(dfs(child,i+1) for child in node.children.values())
                if ch not in node.children:
                    return False
                return dfs(node.children[ch],i+1)
        return dfs(self.root,0)
        


# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```
