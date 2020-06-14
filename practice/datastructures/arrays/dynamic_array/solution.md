# Explanation


# Code
```ruby
#!/bin/ruby
# Complete the dynamicArray function below.
def dynamicArray(n, queries)
  last_answer = 0
  seq_list = []
  n.times {seq_list  << []}
  results = []

  queries.each do |query|
    type, x, y = query

    if type == 1
      # query one
      seq = seq_list[((x ^ last_answer) % n)]
      seq << y
    else
      # query two
      seq = seq_list[((x ^ last_answer) % n)]
      last_answer = seq[y % seq.length]
      results << last_answer
    end
  end

  results
end

fptr = File.open(ENV['OUTPUT_PATH'], 'w')

nq = gets.rstrip.split

n = nq[0].to_i

q = nq[1].to_i

queries = Array.new(q)

q.times do |queries_row_itr|
    queries[queries_row_itr] = gets.rstrip.split(' ').map(&:to_i)
end

result = dynamicArray n, queries

fptr.write result.join "\n"
fptr.write "\n"

fptr.close()
```