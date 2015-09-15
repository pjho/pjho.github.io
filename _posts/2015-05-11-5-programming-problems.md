---
layout: post
title:  "5 Programming Problems"
date:   2015-05-13 12:02:10
tags:   code-exercise ruby
---

excercise source: [blog.svpino.com][link1]


1) Write three functions that compute the sum of the numbers in a given list
   using a for-loop, a while-loop, and recursion.

~~~ruby

list = [3,5,12]

def for_loop(sum, list)
  list.each { |i| sum += i }
  return sum

  # Actual ruby for loop
  # for i in list
  #   sum += i
  # end
  # return sum
end

puts "for_loop : #{for_loop(0, list)}"

def while_loop(sum, list)
  i = 0
  while i < list.length
    sum += list[i]
    i += 1
  end
  return sum
end

puts "while_loop : #{while_loop(0, list)}"


def recursion(sum, list, i)
  sum += list[i]

  if i < list.length - 1
    i+=1
    recursion(sum, list, i)
  else
    return sum
  end

end

puts "recursion : #{ recursion(0, list, 0) }"

~~~

2) Write a function that combines two lists by alternatingly taking elements.
   For example: given the two lists [a, b, c] and [1, 2, 3], the function should return [a, 1, b, 2, c, 3].


~~~ruby

def merge_lists(list_1, list_2)
  i = 0
  merged_list = []
  # + array lengths, + 1 & div by 2 to allow for different lengths & int rounding down
  while i < (list_1.length + list_2.length + 1) / 2
    merged_list.push( list_1[i] || nil)
    merged_list.push( list_2[i] || nil)
    i += 1
  end
  return merged_list
end
# puts merge_lists(['a', 'b', 'c','d'],[1, 2, 3, 4])


~~~
3) Write a function that computes the list of the first 100 Fibonacci numbers.
By definition, the first two numbers in the Fibonacci sequence are 0 and 1,
and each subsequent number is the sum of the previous two.
As an example, here are the first 10 Fibonnaci numbers: 0, 1, 1, 2, 3, 5, 8, 13, 21, and 34.

~~~ ruby

def fibonacci(a, b, i)
  # Manually print the first numbers if 1st iteration
  print "1: 0 \n2: 1 \n" if i == 2

  c = a + b
  print "#{i}: #{c} \n"

  if i < 100
    fibonacci(b, c, i+=1)
  end
end

fibonacci(0, 1, 2)

~~~

4) Write a function that given a list of non negative integers,
arranges them such that they form the largest possible number.
For example, given [50, 2, 1, 9], the largest formed number is 95021.

~~~ ruby
puts [50,2,1,9].map { |i| i.to_s }.sort.reverse.reduce(:+).to_i
puts [420,42,423].map { |i| i.to_s }.sort.reverse.reduce(:+).to_i
# Nope. Doesn't work. :(
~~~



5) Write a program that outputs all possibilities to put + or - or nothing between
the numbers 1, 2, ..., 9 (in this order) such that the result is always 100.
For example: 1 + 2 + 34 – 5 + 67 – 8 + 9 = 100.

~~~ ruby
# Nope. One day.
~~~

[link1]: https://blog.svpino.com/2015/05/07/five-programming-problems-every-software-engineer-should-be-able-to-solve-in-less-than-1-hour

