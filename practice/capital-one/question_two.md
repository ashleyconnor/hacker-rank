```ruby

class LinkedListNode

  attr_accessor :val, :next

  def initialize(node_value)
    @val = node_value
    @next = nil
  end
end

def _insert_node_into_singlylinkedlist(head, tail, val)
  if head == nil
    head = LinkedListNode.new(val)
    tail = head
  else
    node = LinkedListNode.new(val)
    tail.next = node
    tail = tail.next
  end
  return tail
end

def removeNodes(list, x)
  head = list

  while list.next do
    if list.next.val > x
        list.next = list.next.next
    else
      list = list.next
    end
  end

  head.val > x ? head.next : head
end
```