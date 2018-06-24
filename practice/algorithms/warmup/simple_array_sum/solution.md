# Explanation

In ruby the array data-structure can take advantage of the [Enumerable](https://ruby-doc.org/core-2.5.1/Enumerable.html) mixin which implements a reduce method.

Reduce can take a symbol with the method name we want to run.

In this case we are passing the plus operator which will add all elements in the array returning the result.

# Code

```ruby
#!/bin/ruby

#
# Complete the simpleArraySum function below.
#
def simpleArraySum(ar)
    ar.reduce(:+)
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

ar_count = gets.to_i

ar = gets.rstrip.split(' ').map(&:to_i)

result = simpleArraySum ar

fptr.write result
fptr.write "\n"

fptr.close()
```