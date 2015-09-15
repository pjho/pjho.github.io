---
layout: post
title:  "The Name Game"
date:   2015-05-11 20:02:10
tags: code-exercise ruby
---

[http://www.reddit.com/r/dailyprogrammer/the-name-game][link1]


> Come on everybody! I say now let's play a game I betcha I can make a rhyme out of anybody's name
> The first letter of the name, I treat it like it wasn't there But a "B" or an "F" or an "M" will appear
> And then I say "bo", add a "B", then I say the name  and "Bonana fanna" and a "fo"
> And then I say the name again with an "F" very plain and a "fee fy" and a "mo"
> And then I say the name again with an "M" this time and there isn't any name that I can't rhyme
> But if the first two letters are ever the same, I drop them both and say the name like
> Bob, Bob drop the B's "Bo-ob" For Fred, Fred drop the F's "Fo-red" For Mary, Mary drop the M's Mo-ary
> That's the only rule that is contrary.


**input:**
&nbsp;&nbsp;&nbsp;&nbsp; *Lincoln*
**output:**
&nbsp;&nbsp;&nbsp;&nbsp;Lincoln, Lincoln bo Bincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Bonana fanna fo Fincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Fee fy mo Mincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Lincoln!

To test all cases use: *`Anna, Dave, Bob, Fred, Mary`*

~~~ruby
class Rhyme

  def initialize(name)
    @name = name
    @rhymed_names = { "B" => [], "F" => [], "M" => [] }
    self.process_rhyme_names
  end

  # @method process_rhyme_names
  # Converts Name to the rhymed version for each letter
  # and stores to global rhymed_names hash
  def process_rhyme_names

    @rhymed_names.each do |letter, val|

      # the seperator word will be #{letter}o unless letter is the first
      # letter of name. In which case return #{letter}o-
      sep = letter == @name[0].upcase ? letter + 'o-' : letter.downcase + 'o '

      # Set rhyme name based on whether name starts with
      # a Consonant, B, M or F, or a vowel
      rname = if letter == @name[0].upcase
                @name[1..-1]
              elsif /[aeiou]/.match(@name[0].downcase).nil?
               # If vowel.match = nil i.e. a consonant
                letter + @name[1..-1]
              else
                letter + @name.downcase
              end

      @rhymed_names[letter].push(sep,rname)

    end
  end

  # @method output_rhyme
  # Prints Rhyme to screen
  def output_rhyme
    # Set rhymed_name containers to letter variables for convenience
    b = @rhymed_names['B']
    f = @rhymed_names['F']
    m = @rhymed_names['M']

    # Output Rhymed Name
    puts "#{@name}, #{@name} #{ b[0] + b[1] },"
    puts "Bonana fanna #{ f[0] + f[1] },"
    puts "Fee fy #{ m[0] + m[1] },"
    puts "#{@name}!"
  end

end # End of class rhyme

# puts "Please enter your name..."
# name = $stdin.gets.chomp
# rhyme = Rhyme.new(name)
# rhyme.output_rhyme
["Dave","Anna","Bob","Fred","Mary"].each do |name|
  rhyme = Rhyme.new(name)
  rhyme.output_rhyme
  puts "----------------------\n"
end

~~~



[link1]: http://www.reddit.com/r/dailyprogrammer/comments/338p28/20150420_challenge_211_easy_the_name_game/

