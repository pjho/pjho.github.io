---
layout: post
title:  "The Button can be pressed but once..."
date: 2015-05-21 09:05:10
tags: code-exercise ruby
---

####The Challenge
> The 1st of April brought [the Button][link1] to Reddit - if you've not heard of it,
read the blog post on it [here][link2] . The value of the countdown at the instant
that someone presses the button determines the flair that they obtain on the
subreddit. For example, if the counter is at 53.04 seconds, then I would obtain
a 53 flair, as that is the number of seconds (rounded down). After a person
presses the button, the countdown resets from 60.00 seconds. Today's challenge
is simple - you'll be given a list of users in no particular order, and told
at which time each user pressed the button; you'll need to work out which
flair each user gets.  You can assume that the countdown never runs to zero
for this challenge, and that no two users will press the button at exactly
the same moment.

src [/r/dailyprogrammer/the-button][src]

~~~ ruby

## input            ## output
# 7                 #
# UserA: 41.04      # UserB: 52
# UserB: 7.06       # UserE: 54
# UserC: 20.63      # UserC: 51
# UserD: 54.28      # UserF: 49
# UserE: 12.59      # UserA: 50
# UserF: 31.17      # UserD: 46
# UserG: 63.04      # UserG: 51


def get_flair(input)

  # Process input string of users to a hash sorted by user's score
  users = {}
  input.strip.split("\n")[1..-1].each do |u|
     user = u.split(':').map(&:strip)
     users[user[0]] = user[1].to_f.round(2)
  end
  users = users.sort_by { |k, v| v }.to_h

  # Process users' flair scores and add to output string
  prev = 0
  output = ""
  users.each do |user|
    output << "#{user[0]}: #{ (60 - (user[1] - prev)).to_i} \n"
    prev = user[1]
  end

  return output
end


input = "8
      	 Coder_d00d: 3.14
         Cosmologicon: 22.15
         Elite6809: 17.25
         jnazario: 33.81
         nint22: 10.13
         rya11111: 36.29
         professorlamp: 31.60
         XenophonOfAthens: 28.74"

puts get_flair(input)

~~~

&nbsp;

#### Other People's Code

~~~ ruby

## aust1nz
# I really like this solution for it's clarity
# variables are better named than mine.
# The user class is a nice & logical approach to processing user info
# Input method is nice and makes use of the otherwise redundant first line
# <=> Combined comparison operator. a > b ? 1 : a < b ? -1 : 0

class User
  attr_reader :time
  def initialize(name, time)
    @name = name
    @time = time.to_f
  end

  def set_flair(last_clicked)
    @flair = (60 - (time - last_clicked)).floor
  end

  def to_s
    "#{@name}: #{@flair}"
  end
end

users = Array.new
last_clicked = 0

gets.chomp.to_i.times do
  string = gets.chomp.split(": ")
  users.push(User.new(string[0], string[1]))
end

users.sort! { |a,b| a.time <=> b.time }

users.each do |user|
  user.set_flair(last_clicked)
  last_clicked = user.time
end

puts users

~~~



[src]: http://www.reddit.com/r/dailyprogrammer/comments/31ls3h/20150406_challenge_209_Easy_the_button_can_be/
[link1]: http://www.reddit.com/r/thebutton
[link2]: http://www.redditblog.com/2015/04/the-button.html
