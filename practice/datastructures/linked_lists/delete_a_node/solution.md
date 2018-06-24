# Explanation

We take care of the base case which is removal of head. In this case we return the list without the head.

Then loop through the list until we hit the position we wish to remove. Then we change the pointer to that node to the one after. Break the loop since we are only removing 1 node and we have done so.

If this node is not the node preceding the one to be removed, increment the position and move the current list pointer.

# Code

```ruby
def deleteNode(llist, position)
  current_position = 1
  head = llist

  if position == 0
      return llist.next
  end

  while llist.next do
      if current_position == position
          llist.next = llist.next.next
          break
      else
          llist = llist.next
          current_position += 1
      end
  end
  head
end
```