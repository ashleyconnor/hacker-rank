# Explanation

This involves looping through the array of arrays keeping track of both the first and second diagonal positions.

I am using another `Enumerable` method `each_with_index` which passes the element and it's index.

We then add the result of `row[idx]` element to the first diagnol like so:

e.g. In a 4x4 grid we want to write a program that will give us elements

(0,0) - (1,1) - (2,2) - (3,3) for diagonal 1
(3,0) - (2,1) - (1,2) - (0,3) for diagonal 2

```
1 # # 4 <- 0
# 2 3 # <- 1
# 2 3 # <- 2
1 # # 4 <- 3
^ ^ ^ ^
| | | |
0 1 2 3
```

On the first pass row is 0 and idx is 0 so `row[idx]` gives us value 1 (0,0 on the grid) and `row[zb_length - idx]` gives us the value 4.

Evertually we will get `first_diagonal = (1 + 2 + 3 + 4)` and `second_diagonal = (4 + 3 + 2 + 1)`.

We subtract these numbers from each other to get `0`. In the case when the result is negative, the `.abs` method will give us a positive number.

```ruby
-2.abs
=> 2
```

# Code

```ruby
#!/bin/ruby

require 'json'
require 'stringio'

# Complete the diagonalDifference function below.
def diagonalDifference(arr)
    first_diagonal = 0
    second_diagonal = 0
    zb_length = arr.length - 1 # zero based length

    arr.each_with_index do |row, idx|
        first_diagonal += row[idx]
        second_diagonal += row[zb_length - idx]
    end

    (first_diagonal - second_diagonal).abs
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

n = gets.to_i

arr = Array.new(n)

n.times do |i|
    arr[i] = gets.rstrip.split(' ').map(&:to_i)
end

result = diagonalDifference arr

fptr.write result
fptr.write "\n"

fptr.close()
```