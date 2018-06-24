# Day 24: More Linked Lists

## Summary
Remove duplicates from Linked List.

### Solution

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

### Explanation
Removing duplicates essentially involves moving the pointer of the initial node that contains a duplicated value to point to
a node that does not contain a duplicate value.

To do this we loop through the entire list checking if the next node exists and does it contain a duplicate value. If it does
we remove that node by linking around it to it's next value, thus unlinking the dupe.

If we have removed a dupe we need to loop using the same node as the next node may also be duplicated.

If the next node is not duplicated we can update to the next node and continue looping through the list.

### Comments
Made easy by the fact that the Linked List is sorted by ascending order based on data value.

### URL
https://www.hackerrank.com/challenges/30-linked-list-deletion/problem
