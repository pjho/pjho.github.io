---
layout: post
title:  "Culling Numbers"
date: 2015-05-26 10:07:10
tags: code ruby
---

####The Challenge
>Numbers surround us. Almost too much sometimes.  
>It would be good to just cut these numbers down and cull out the repeats.  
>Given some numbers let us do some number "culling".  
>**Input:**  
>You will be given many unsigned integers.  
>**Output:**  
>Find the repeats and remove them. Then display the numbers again.  
 
src [/r/dailyprogrammer/EasyCullingNumbers][src]

~~~ ruby
# Ruby makes this too easy so I tried to come up with 5 different examples

input = "12 23 12 2 3 54 6 21 9 23"

## 1)
# Ruby is beautiful
puts input.split.uniq.join(' ')

## 2)
# With an each loop
output = []
input.split.each { |i| output.push i unless output.include? i }
puts output.join(' ')

## 3)
# Only strings
out = ""
input.scan(/\d+/) { |i| out << "#{i} " if out.index(/\b#{i}\b/).nil? }
puts out

## 4)
# while loop modifying string
i, o = input, []
while l = i.index(' ')
  d = i[0..l]
  i = i[l+1..-1]
  o.push d unless o.include? d
end
puts o.join

## 5)
# regex: order of output is different since this matches the last
#    occurance of a repeated number & negative look behind is problematic
puts input.scan(/\b(\d+)\b(?!.*\b\1\b)/).join(' ')

~~~


[src]: http://www.reddit.com/r/dailyprogrammer/comments/30ubcl/20150330_challenge_208_Easy_culling_numbers/
