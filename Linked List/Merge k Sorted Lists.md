# Merge k Sorted Lists
``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def merge2(self, list1: Optional[ListNode], list2: Optional[ListNode])-> Optional[ListNode]:
        dummy=ListNode()
        tails=dummy
        while list1 is not None and list2 is not None:
            if list1.val<list2.val:
                tails.next=list1
                list1=list1.next
            else:
                tails.next=list2
                list2=list2.next
            tails=tails.next
        if list1 is not None:
            tails.next = list1
        elif list2 is not None:
            tails.next = list2
        return dummy.next 

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if not lists:
            return None
        return self.merge_recursive(lists, 0, len(lists) - 1)
    def merge_recursive(self, lists: List[Optional[ListNode]],start: int, end:int) -> Optional[ListNode]:
        mid=(start+end)//2
        if start == end:
            return lists[start]
        
        
        if start > end:
            return None
        left=self.merge_recursive(lists,start,mid)
        right=self.merge_recursive(lists,mid+1,end)
        return self.merge2(left,right)
```
