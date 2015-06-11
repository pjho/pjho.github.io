---
layout: post
title:  "Ruby Koans"
date: 2015-06-11 13:29:10
tags: code ruby
---

####The Challenge
> The Koans walk you along the path to enlightenment in order to learn Ruby. The goal is to learn the Ruby language, syntax, structure, and some common functions and libraries. We also teach you culture. Testing is not just something we pay lip service to, but something we live. It is essential in your quest to learn and do great things in the language.

src: [rubykoans.com](http://rubykoans.com)

Below are my solutions to the challenges in the Koans. Much of the rest of the exercise involved fixing tests while walking through all areas of the Ruby language. While a lot of what was covered was revision there were certainly lots of things I learned particularly in the Classes, Modules, Inheritance & Scope modules.

My full output of the koans can be [viewed on github](https://github.com/pjho/learning_ruby/tree/master/koans)


~~~ruby

# Triangle analyzes the lengths of the sides of a triangle
# (represented by a, b and c) and returns the type of triangle.
#
# It returns:
#   :equilateral  if all sides are equal
#   :isosceles    if exactly 2 sides are equal
#   :scalene      if no sides are equal

# My Solution

def my_triangle(a, b, c)
    case [a,b,c].uniq.length
      when 3
        :scalene
      when 2
        :isosceles
      when 1
        :equilateral
    end
end


# A better solution

def triangle(a, b, c)
  a, b, c = [a, b, c].sort
  raise TriangleError if a <= 0 || a + b <= c
  [:equilateral, :isosceles, :scalene][[a, b, c].uniq.size - 1]
end

~~~





#### about.scoring.project.rb
~~~ruby

# Greed is a dice game where you roll up to five dice to accumulate
# points.  The following "score" function will be used to calculate the
# score of a single roll of the dice.
#
# A greed roll is scored as follows:
# * A set of three ones is 1000 points
# * A set of three numbers (other than ones) is worth 100 times the
#   number. (e.g. three fives is 500 points).
# * A one (that is not part of a set of three) is worth 100 points.
# * A five (that is not part of a set of three) is worth 50 points.
# * Everything else is worth 0 points.

# My Solution

def score(dice)
  score = 0;

  (1..6).each do |num|
    occurances = dice.select{ |i| i == num }.size
    multiplier = num == 1 ? 1000 : 100

    if occurances >= 3
      score += num * multiplier
      occurances -= 3
    end

    if num == 1
      score += occurances * 100
    elsif num == 5
      score += occurances * 50
    end
  end
  score
end

# A better solution - Use modulus to find remainder

def score (dice)
    sum = 0
    (1..6).each do |i|
        idice = dice.select { |d| d == i }
        if idice.size >= 3
            sum += (i==1 ? 1000 : i*100)
        end
        sum += (idice.size % 3) * 100   if i == 1
        sum += (idice.size % 3) *  50   if i == 5
    end
    sum
end

~~~


about.dice.project.rb

~~~ruby
# Implement a DiceSet Class here:

class DiceSet
  attr_reader :values

  def roll(count=1)
    @values = count.times.map{ rand(1..6) }
  end
end
~~~


####about.proxy.object.project.md

~~~ruby

# Project: Create a Proxy Class
#
# In this assignment, create a proxy class (one is started for you
# below).  You should be able to initialize the proxy object with any
# object.  Any messages sent to the proxy object should be forwarded
# to the target object.  As each message is sent, the proxy should
# record the name of the method sent.
#
# The proxy class is started for you.  You will need to add a method
# missing handler and any other supporting methods.  The specification
# of the Proxy class is given in the AboutProxyObjectProject koan.

class Proxy
  attr_reader :messages

  def initialize(target_object)
    @object = target_object
    @messages = []
    @called = {}
  end

  def method_missing(method_name, *args, &block)
    if @object.respond_to?(method_name)
      @messages << method_name
      @called[method_name] = @called[method_name].nil? ? 1 : @called[method_name] += 1
      @object.send(method_name, *args)
    else
      super(method_name, *args, &block)
    end
  end

  def called?(method_name)
    @called.keys.include?(method_name)
  end
  
  def number_of_times_called(method_name)
    @called[method_name].nil? ? 0 : @called[method_name] 
  end
end

~~~

####that is all

~~~ruby
                                  ,,   ,  ,,
                                :      ::::,    :::,
                   ,        ,,: :::::::::::::,,  ::::   :  ,
                 ,       ,,,   ,:::::::::::::::::::,  ,:  ,: ,,
            :,        ::,  , , :, ,::::::::::::::::::, :::  ,::::
           :   :    ::,                          ,:::::::: ::, ,::::
          ,     ,:::::                                  :,:::::::,::::,
      ,:     , ,:,,:                                       :::::::::::::
     ::,:   ,,:::,                                           ,::::::::::::,
    ,:::, :,,:::                                               ::::::::::::,
   ,::: :::::::,       Mountains are again merely mountains     ,::::::::::::
   :::,,,::::::                                                   ::::::::::::
 ,:::::::::::,                                                    ::::::::::::,
 :::::::::::,                                                     ,::::::::::::
:::::::::::::                                                     ,::::::::::::
::::::::::::                      Ruby Koans                       ::::::::::::
::::::::::::                   (in Ruby 2.2.2)                    ,::::::::::::
:::::::::::,                                                      , :::::::::::
,:::::::::::::,                brought to you by                 ,,::::::::::::
::::::::::::::                                                    ,::::::::::::
 ::::::::::::::,                                                 ,:::::::::::::
 ::::::::::::,               Neo Software Artisans              , ::::::::::::
  :,::::::::: ::::                                               :::::::::::::
   ,:::::::::::  ,:                                          ,,:::::::::::::,
     ::::::::::::                                           ,::::::::::::::,
      :::::::::::::::::,                                  ::::::::::::::::
       :::::::::::::::::::,                             ::::::::::::::::
        ::::::::::::::::::::::,                     ,::::,:, , ::::,:::
          :::::::::::::::::::::::,               ::,: ::,::, ,,: ::::
              ,::::::::::::::::::::              ::,,  , ,,  ,::::
                 ,::::::::::::::::              ::,, ,   ,:::,
                      ,::::                         , ,,
                                                  ,,,
                                                  
                                                  
~~~
