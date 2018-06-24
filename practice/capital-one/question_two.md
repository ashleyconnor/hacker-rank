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

tail = nil
list = nil

[5,2,1,6,7].each_with_index do |val, idx|
  if idx == 0
    list = _insert_node_into_singlylinkedlist(list, tail, val)
    tail = list
  else
    tail = _insert_node_into_singlylinkedlist(list, tail, val)
  end
end

[1,2,3,4,5].each_with_index do |val, idx|
  if idx == 0
    list = _insert_node_into_singlylinkedlist(list, tail, val)
    tail = list
  else
    tail = _insert_node_into_singlylinkedlist(list, tail, val)
  end
end

def removeNodes(list, x)
  #list - Linked List (head)
  #x - value which to remove (if <)

  # loop through nodes keep reference to previous node
  # if next node is > X replace reference to that node with node after
  # continue loop

  head = list

  while list.next do
    if list.next.val > x
        list.next = list.next.next
    end

    # remove tail
    if list.next.val > x
        list.next = nil
    else
        list = list.next
    end
  end

  head.val > x ? head.next : head
end
```