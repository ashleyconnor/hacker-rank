```ruby
#!/bin/ruby

require 'json'
require 'stringio'

# Complete the camelcase function below.
def camelcase(s)
  uppercase = /[A-Z*]/
  s.scan(uppercase).length + 1
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

s = gets.to_s.rstrip

result = camelcase s

fptr.write result
fptr.write "\n"
fptr.close()
```