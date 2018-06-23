# Explanation

I created a hash to convert the hours and mins to english words, since my algorithm relies on next hour I include an entry for the wraparound `13` which points back to the word `one`.

There's also a lot of cases to deal with here:

0 - o' clock
1 - one minute past (notice no plural on minute)
15 - quarter
30 - half
45 - quarter to
59 - one minute to
2..30 - minutes past
30..59 - minutes to

I rely mostly on the fact that a case statement will return early so our `15` match will no make it to the second to last case.

When minutes is over `30` we require the next hour and we need to know how many minutes until the hour is complete `(60 - mins)`, except in the case of `quarter to`.

# Thoughts

Surprised this was medium. I've seen much harder easy problems on the site.

# Code
```ruby
#!/bin/ruby

require 'json'
require 'stringio'

hours = {
  1 => "one",
  2 => "two",
  3 => "three",
  4 => "four",
  5 => "five",
  6 => "six",
  7 => "seven",
  8 => "eight",
  9 => "nine",
  10 => "ten",
  11 => "eleven",
  12 => "twelve",
  13 => "one" # wrap around clock
}

mins = hours.merge({
  13 => "thirteen",
  14 => "fourteen",
  16 => "sixteen",
  17 => "seventeen",
  18 => "eighteen",
  19 => "nineteen",
  20 => "twenty",
  21 => "twenty one",
  22 => "twenty two",
  23 => "twenty three",
  24 => "twenty four",
  25 => "twenty five",
  26 => "twenty six",
  27 => "twenty seven",
  28 => "twenty eight",
  29 => "twenty nine"
})

# Complete the timeInWords function below.
def timeInWords(h, m)
    hour = hours[h]
    next_hour = hours[(h + 1)]

    case m
      when 0
          "#{hour} o' clock"
      when 1
          "one minute past #{hour}"
      when 15
          "quarter past #{hour}"
      when 30
          "half past #{hour}"
      when 45
          "quarter to #{next_hour}"
      when 59
          "one minute to #{next_hour}"
      when 2...30
          minutes = mins[m]
          "#{minutes} minutes past #{hour}"
      when 30...59
          minutes = mins[(60 - m)]
          "#{minutes} minutes to #{next_hour}"
    end
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

h = gets.to_i

m = gets.to_i

result = timeInWords h, m

fptr.write result
fptr.write "\n"

fptr.close()
```