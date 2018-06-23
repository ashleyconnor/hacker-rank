
# Code without std lib
```ruby
#!/bin/ruby

require 'json'
require 'stringio'

nd = gets.rstrip.split

n = nd[0].to_i

d = nd[1].to_i

a = gets.rstrip.split(' ').map(&:to_i)

# brute force
# O(n * a)
n.times do
  new_array = []
  a.each_with_index {|ele, idx| new_array.insert(idx - 1, ele) }
  a = new_array
end

puts a.join(" ")

# direct
# O(n)
new_array = Array.new(n)
a.each_with_index {|ele, idx| new_array[idx - d] = ele }

puts new_array.join(" ")
```

# Code using std lib
```ruby
#!/bin/ruby

require 'json'
require 'stringio'

nd = gets.rstrip.split

n = nd[0].to_i

d = nd[1].to_i

a = gets.rstrip.split(' ').map(&:to_i)

puts a.rotate(d).join(" ")
```