```python
def insertNodeAtTail(head, data):
  list = head
  new_node = SinglyLinkedListNode(data)

  while list.next():
    if list.next() == None:
        list.next = new_node
        break
    else:
        list = list.next()
  head
```