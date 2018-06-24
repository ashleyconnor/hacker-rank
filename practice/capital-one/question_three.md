```ruby

def maximumSum(arr)
    max_so_far = 0
    max_ending_here = 0

    arr.each do |element|
        max_ending_here = [max_ending_here + element, 0].max
        max_so_far = [max_ending_here, max_so_far].max
    end

    max_so_far
end
```