# Explanation

Pretty simple.

We break the string into units using a regular expression and 4 capture groups:

1. hours
2. minutes
3. seconds
4. period (AM/PM)

/(\d{2}):(\d{2}):(\d{2})(AM|PM)/
  ^                      ^
  ^                      capture AM or PM
  ^
  match exactly 2 digits \d{2}

Hours and period is what we really care about as we will modifying the hours based on the period input.

Minutes and seconds stay static.

Once we have captured our groups we convert the hours to an integer so we can perform comparison operators on it.

Next we test for the edgecase of midnight. 12:00:00AM is the only AM hour that requires converting (to 0), otherwise we can let it fall through.

Next we check if we are in the PM period. If we are we add 12 to the hours unit with the exception of 12 which remains the same (12:00:00PM == 12:00:00 24hr clock).

We then prepend 0 to single digit hours and return the formatted string.

# Code

```ruby
#!/bin/ruby

#
# Complete the timeConversion function below.
#

def matchTime(string)
    regex = /(\d{2}):(\d{2}):(\d{2})(AM|PM)/
    match = string.match regex
    match.captures
end

def timeConversion(s)
    hours, minutes, seconds, period = matchTime(s)
    hours = hours.to_i

    if period == "AM" and hours == 12
        hours = 0
    elsif period == "PM" and hours < 12
        hours += 12
    end

    hours = hours.to_s.rjust(2, "0")

    "#{hours}:#{minutes}:#{seconds}"
end

fp = File.open(ENV['OUTPUT_PATH'], 'w')

s = gets.to_s.rstrip

result = timeConversion s

fp.write result
fp.write "\n"

fp.close()
```