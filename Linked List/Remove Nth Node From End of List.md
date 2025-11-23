# Remove Nth Node From End of List
## Using TWo Pointers (Slow and Fast)
``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        if not head:
            return None
        dummy=ListNode()
        dummy.next=head
        slow=dummy
        fast=dummy
        for i in range(n):
            fast=fast.next
        while fast.next!=None:
            fast=fast.next
            slow=slow.next
        slow.next = slow.next.next
        
        return dummy.next

```
