# Explanation



# Code

```ruby
def maxSubarray(arr)
    sub_max_sum_so_far = -10 ** 4
    seq_max_sum = -10 ** 4
    sub_max_sum_ending_here = 0

    arr.each do |element|
        seq_max_sum ||= element
        sub_max_sum_so_far ||= element

        seq_max_sum = [seq_max_sum + element, element, seq_max_sum].max

        sub_max_sum_ending_here = [sub_max_sum_ending_here + element, element].max
        sub_max_sum_so_far = [sub_max_sum_ending_here, sub_max_sum_so_far].max
    end

    [sub_max_sum_so_far, seq_max_sum]
end
```