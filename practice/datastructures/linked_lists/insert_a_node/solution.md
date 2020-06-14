# Explanation

We take care of the base case which is creating a new node as head and pointing next to the existing list.

Otherwise we loop through the list keeping our position.

When we are the node before the insertion point we point that node to our new node and then point our new nodes next to the node that would have come after this.

# Code

```ruby
def insertNodeAtPosition(llist, data, position)
  current_position = 1
  head = llist
  node_to_be_inserted = SinglyLinkedListNode.new(data)

  if position == 0
    node_to_be_inserted.next = llist
    return node_to_be_inserted
  end

  while llist.next do
    if current_position == position
        node_to_be_inserted.next = llist.next
        llist.next = node_to_be_inserted
        break
    else
        llist = llist.next
        current_position += 1
    end
  end
  head
end
```