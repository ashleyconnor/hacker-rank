# Day 24: More Linked Lists

## Summary: Remove duplicates from Linked List

```python3
    def removeDuplicates(self, head):
        temp_head = head # keep a reference to head for returning
        while temp_head: # while node is not last node
            if temp_head.next and temp_head.data == temp_head.next.data:
                # if current node and next node have same data value
                # update next node to the node after next or None
                if temp_head.next.next:
                    temp_head.next = temp_head.next.next
                else:
                    temp_head.next = None
            else:
              # otherwise no duplicate detected to move pointer to next node
              temp_head = temp_head.next
        return head
```

Made easy by the fact that the Linked List is sorted by ascending order based on data value.

URL: https://www.hackerrank.com/challenges/30-linked-list-deletion/submissions/code/
