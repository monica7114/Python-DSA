# Reorder List
# 3 Step:
   1. Finding Middle (using Slow and Fast Pointers)
   2. Reversing the 2nd Half
   3. Add ALternated Nodes freon two Linked List
``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        if not head or not head.next:
            return
        fast=head
        slow=head
        while fast is not None and fast.next is not None:
            fast=fast.next.next
            slow=slow.next
        head1=head
        head2=slow.next
        slow.next=None
        prev=None
        current = head2
        while current is not None:
            new_node=current.next
            current.next=prev
            prev=current
            current=new_node
        head2_reversed = prev
        while head2_reversed:
            temp1 = head1.next
            temp2 = head2_reversed.next
    
     
            head1.next = head2_reversed
            head2_reversed.next = temp1
            
            
            head1 = temp1
            head2_reversed = temp2

```
