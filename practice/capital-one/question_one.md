```ruby

def fizzBuzz(n)
  n.times do |num|
    num += 1 # zero indexed counter

    if num % 3 == 0 and num % 5 == 0
      puts "FizzBuzz"
    elsif num % 3 == 0
      puts "Fizz"
    elsif num % 5 == 0
      puts "Buzz"
    else
      puts num
    end
  end
end

```