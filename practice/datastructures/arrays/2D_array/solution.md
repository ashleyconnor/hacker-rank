# Explanation
Since the grid is known to be 6x6 we can hard code the loop values `4.times`

# Code

```ruby
#!/bin/ruby

require 'json'
require 'stringio'

# Complete the hourglassSum function below.
def hourglassSum(arr)
  max = -4611686018427387903
  4.times do |i|
    4.times do |j|
      current =
          arr[i][j] + arr[i][j + 1] + arr[i][j + 2] \
                    + arr[i + 1][j + 1] + \
          arr[i + 2][j] + arr[i + 2][j + 1] + arr[i + 2][j + 2]
        max = current if current > max
      end
  end
  max
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

arr = Array.new(6)

6.times do |i|
    arr[i] = gets.rstrip.split(' ').map(&:to_i)
end

result = hourglassSum arr

fptr.write result
fptr.write "\n"

fptr.close()
```