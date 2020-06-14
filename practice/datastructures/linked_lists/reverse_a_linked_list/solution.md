```ruby
def reverse(head)
    _next = nil
    _prev = nil
    _current = head

    while _current do
        _next = _current.next
        _current.next = _prev
        _prev = _current
        _current = _next
    end
    _prev
end
```