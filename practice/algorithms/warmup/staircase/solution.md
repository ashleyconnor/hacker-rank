# Explanation

# Code
```ruby
#!/bin/ruby

require 'json'
require 'stringio'

# Complete the staircase function below.
def staircase(n)
    n.times do |num|
      puts(" " * (n - (num + 1)) + "#" * (num + 1))
    end
end

n = gets.to_i

staircase n
```