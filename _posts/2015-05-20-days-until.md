---
layout: post
title:  "Counting the days until..."
date:   2015-05-20 12:02:10
tags:   code-exercise ruby
---

####The Challenge
> Sometimes you wonder. How many days I have left until.....
> Whatever date you are curious about. Maybe a holiday. Maybe a vacation.
> Maybe a special event like a birthday.
> So today let us do some calendar math. Given a date that is in the future how
> many days until that date from the current date?

src: [/r/dailyprogrammer/days-until][src]

~~~ruby
##
# Most of the time on this was spent playing and researching date functions
# in ruby and how they respond to different formats.
##


# require chronic for research method. Not required for this challenge.
require 'chronic'

# Returns the difference in days btn now and a given date or nil
# In production would require validation of date and use strptime
def days_until(date)
  return (Date.parse(date) - Time.new.to_date).to_i rescue nil
end

# Get date from user
puts "Enter a date in the format DD-MM-YYYY"
days = days_until(gets.chomp)

unless days.nil?
  puts "#{days.abs}  #{days > 0 ? "days to go. " : " days ago."}"
else
  puts "Your date format was incorrect."
end


# ================================================================= #

# This function is just playing around with date & time in Ruby
# as I haven't dne so before.
def days_until_research(date)

  # Dates with spaces don't parse well so replace with -
  # Chronic can't handle e.g. July-10-2020 though
  # tldr - Know your date format
  formatted_date = date.gsub(/\s/,"-")

  # Testing Now
  now = Time.now.to_date
  puts "It is currently #{now}"
  puts "That is #{now.strftime("%d %m %Y")}"


  # Testing .parse
  puts "the supplied date is #{date}"

  raw = Date.parse(date) rescue nil
  puts "the parsed raw date is #{raw}"

  formatted = Date.parse(formatted_date) rescue nil
  puts "the parsed formatted date is #{formatted}"

  c_raw = Chronic.parse(date)
  puts "the Chronic parsed raw date is #{c_raw}"

  c_formatted = Chronic.parse(formatted_date)
  puts "the Chronic parsed formatted date is #{c_formatted}"


  # Testing .strptime()
  strptime = Date.strptime(date,"%Y %m %d") rescue "error"
  puts "strptime requires you know the format: #{strptime}"


  # Date Math

  # now = Time.now
  future = Date.parse(formatted_date)

  puts "date is in the future?: #{future > now}"


  diff = future - now
  puts "Difference: #{diff.to_i} days."

  return " \n"
end

 puts days_until_research("2015 10 31")


~~~

&nbsp;

#### Other People's Answers

~~~ruby
#!/usr/bin/env ruby


## Things i learnt in this
# - extending a native class
# - Date.today

require 'date'

class Date
  def weekday?
  !(self.saturday? or self.sunday?)
  end
end

def displayUntil(day)
  print "There are #{(day - Date.today).to_i} days left until #{day.to_s}.\n"
  print "#{Date.today.upto(day).count { |d| d.weekday? }} of those are weekdays.\n"
end

while line = gets
  displayUntil(Date.parse(line.chomp))
end

~~~

[src]: http://www.reddit.com/r/dailyprogrammer/comments/2vc5xq/20150209_challenge_201_Easy_counting_the_days/
