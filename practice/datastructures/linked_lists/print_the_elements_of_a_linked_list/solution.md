```python
def printLinkedList(head):
    while head.next:
        print(head.data)
        head = head.next
    print(head.data)
```