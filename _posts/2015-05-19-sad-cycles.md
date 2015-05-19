---
layout: post
title:  "Sad Cycles"
date:   2015-05-19 19:48:10
tags: code ruby
---


####The Challenge

> Take a number, and add up the square of each digit.   
  You'll end up with another number. If you repeat this process over  
  and over you'll end up with a repeating sequence of numbers  
  This sequence is the Sad cycle.  

src: [/r/dailyprogrammer/sad-cycles][src]


~~~ ruby

# My Solution - I made this hard for myself in hindsight.
# - Really not happy with the hardcoded iterations & recursive
#   implementation of sad_cycle
# - I knew there would be a simpler solution to find_sequence
#   but had gone down that route and wanted to write the function
#   to find repetition in the array.

# Finds a Sad Cycle from a given starting number and an exponent
def sad_cycle(start_num, exponent, iterations=100, sequence = [])

  sum = 0

  # loop thru start_num digits multiply by exponent and sum
  start_num.to_s.split('').each do |d| 
    sum += d.to_i**exponent  
  end

  # Add sum to sequence array
  sequence.push(sum)

  # Recursively call the function untill it has run iterations times.
  if iterations > 1
    iterations -=1
    sad_cycle(sum, exponent, iterations, sequence)
  else
    return find_sequence(sequence)
  end

end


# Checks to find a recurring sequence of numbers inside an array
# and returns sequence sub-array if exists
def find_sequence(arr)

  # Loop through array
  arr.each_with_index do |value,index|

    # for each index of array, go through the array to find a value match
    (arr.length - index).times do |i|
      
      offset = index + i

      # When a match is found between the current outer index & an index 
      # further ahead, capture the distance between the values @diff and compare
      # 2 sub arrays
      if value == arr[offset + 1]

        # Diff = distance between matching values in array
        # This is a guess at how long the sequence length is
        diff = offset - index

        # Array 1 starts from outerindex and goes for + @diff cells
        start1 = index
        end1 = index + diff

        # Array 2 starts from the next index after array1 and goes for + @diff cells
        start2 = end1 + 1
        end2 = start2 + diff

        sequence1 = arr[start1..end1]
        sequence2 = arr[start2..end2]
        
        # If the sequences match this is what we're looking for so return it
        if sequence1 == sequence2
          return sequence1.join(", ")
        end
      end

    end # ends inside loop
  end # ends outside loop
  
  return "no match found"
end


# ==============

puts sad_cycle(12,2) # 89, 145, 42, 20, 4, 16, 37, 58
puts sad_cycle(13,2) # 1


~~~

#### Other People's Solutions
I love r/dailyprogrammer for the fact I can look at other solutions to a problem. I've decided to keep them here for reference.

~~~ruby

# http://www.reddit.com/r/dailyprogrammer/comments/
# 36cyxf/20150518_challenge_215_easy_sad_cycles/crdc5ds

sadness, num = gets.to_i, gets.to_i
cycle = []

until cycle.include? num
  cycle << num
  num = num.to_s.chars.map{|n| n.to_i**sadness}.reduce(:+)
end

puts cycle[cycle.index(num)..-1].join(", ")

~~~

&nbsp;

~~~ruby

# http://www.reddit.com/r/dailyprogrammer/comments/
# 36cyxf/20150518_challenge_215_easy_sad_cycles/crd7t77

def b_sad_cycle( base, number )
    seen = []
    while true do
        number = b_sad_number( base, number )
        index = seen.index( number )
        if index == nil
            seen.push( number )
        else
            return seen[ index..-1 ]
        end
    end
end

def b_sad_number ( base, number )
    return number.to_s.chars.reduce( 0 ) { |m, d| m += d.to_i ** base }
end

b = gets.chomp.to_i
n = gets.chomp.to_i
puts b_sad_cycle( b, n ).join( ", " )

~~~

[src]: http://www.reddit.com/r/dailyprogrammer/comments/36cyxf/20150518_challenge_215_easy_sad_cycles/