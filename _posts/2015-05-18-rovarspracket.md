---
layout: post
title:  "Rövarspråket"
date:   2015-05-18 19:34:10
tags:   code-exercise ruby
---

src: [/r/dailyprogammer/Rövarspråket][link1]

Rövarspråket is not very complicated: you take an ordinary word and replace the
consonants with the consonant doubled and with an "o" in between. So the
consonant "b" is replaced by "bob", "r" is replaced with "ror", "s" is replaced
with "sos", and so on. Vowels are left intact. It's made for Swedish, but it
works just as well in English.

~~~ruby
# Encode
# Select all Consonants Replace with \1 o \1
def encode(str)
  return str.gsub(/([b-df-hj-np-tv-z])/i,'\1o\1')
end

# Decode
# find all consonants with $1o$1 and replace with $1
def decode(str)
  return str.gsub(/(?:([b-df-hj-np-tv-z])o\1)/i,'\1')
end

puts "enter string > "
str = gets.chomp
rovarspraket = encode(str)

puts "\n\n" + "Encoded: " + rovarspraket
puts "================="
puts "Decoded: " + decode(rovarspraket)


# END

# http://apidock.com/ruby/String/gsub
# puts "hello".gsub(/([aeiou])/, '<\1>')
# puts "hello".gsub(/./) {|s| s.ord.to_s + ' '}
# puts "hello".gsub(/(?<foo>[aeiou])/, '{\k<foo>}')
# puts 'hello'.gsub(/[eo]/, 'e' => 3, 'o' => '*')
#
# Interesting examples

# Encode
puts $_.gsub(/[b-df-hj-np-tv-xz]/i) { "#$&o#{$&.downcase}" } while gets

# Decode
puts $_.gsub(/([b-df-hj-np-tv-xz])o\1/i, '\1') while gets


# consonant match:  [[^aeiou] && [a-z]]


# gsub(/[qwrtiplkjhgfdszxcvbnm]/i) {|s| s + "o" + s.downcase}

~~~

[link1]:http://www.reddit.com/r/dailyprogrammer/comments/341c03/20150427_challenge_212_Easy_r%C3%8C%C2%A6varspr%C3%8C%C2%B4ket/
