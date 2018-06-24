```ruby
def reversePrint(llist)
  reverse_list = []

  while llist.next() do
      reverse_list.unshift(llist.data)
      llist = llist.next()
  end

  reverse_list.unshift(llist.data)
  reverse_list.each {|n| puts n}
end
```