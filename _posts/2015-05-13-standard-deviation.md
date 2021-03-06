---
layout: post
title:  "Calulating Standard Deviation & SqrRoot"
date: 2015-05-13 12:02:10
tags: code-exercise ruby
---

excercise source: [/r/dailyprogramer/standard-deviation][link1]


Calculate Standard Deviation From Following method

First, calculate the average (or mean) of all your values, which is defined
as the sum of all the values divided by the total number of values in the
population. For our example, the sum of the values is 190 and since there are
10 different values, the mean value is 190/10 = 19

Next, for each value in the population, calculate the difference between it
and the mean value, and square that difference. So, in our example, the first
value is 5 and the mean 19, so you calculate (5 - 19)2 which is equal to 196.
For the second value (which is 6), you calculate (6 - 19)2 which is equal to
169, and so on.

Calculate the sum of all the values from the previous step. For our example,
it will be equal to 196 + 169 + 64 + ... = 956.

Divide that sum by the number of values in your population. The result is
known as the variance of the population, and is equal to the square of the
standard deviation. For our example, the number of values in the population is
10, so the variance is equal to 956/10 = 95.6.

Finally, to get standard deviation, take the square root of the variance. For
our example, sqrt(95.6) ≈ 9.7775.


~~~ruby
def std_dev(pop)
  sum = pop.reduce(:+)
  mean = sum / pop.length.to_f
  difs = pop.map { |i| (i - mean)**2 }
  sum_of_difs = difs.reduce(:+)
  variance = sum_of_difs / pop.length.to_f
  # return Math.sqrt(variance).round(4)
  return sqrt(variance).round(4)
end

def sqrt(number)
  # return Math.sqrt(i) # naaa!
  low = 0.0
  high = number.to_f
  middle = (low + high) / 2
  while abs_dif(middle**2, number)  >  0.0000001
    middle = (low + high) / 2
    if middle**2 > number
      high = middle
    elsif middle**2 < number
      low = middle
    end
  end
  return middle
end

def abs_dif(a,b)
  return (a > b ? a - b : b - a)
end
~~~

~~~ ruby
puts std_dev([5,6,11,13,19,20,25,26,28,37])
# 9.7775

puts std_dev([37, 81, 86, 91, 97, 108, 109, 112, 112, 114, 115, 117, 121, 123, 141])
# 23.2908

puts std_dev([266, 344, 375, 399, 409, 433, 436, 440, 449, 476, 502, 504, 530, 584, 587])
# 83.6616

puts std_dev([809, 816, 833, 849, 851, 961, 976, 1009, 1069, 1125, 1161, 1172, 1178,
              1187, 1208, 1215, 1229, 1241, 1260, 1373])
# 170.1273


~~~



[link1]: http://www.reddit.com/r/dailyprogrammer/comments/35l5eo/20150511_challenge_214_Easy_calculating_the/

