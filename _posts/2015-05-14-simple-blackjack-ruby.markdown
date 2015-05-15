---
layout: post
title:  "Simple BlackJack Game in Ruby"
date:   2015-05-14 19:02:10
categories: code
tags: ruby
thing: rthis
excerpt: "Simple BlackJack game"
---

{% highlight ruby %}
  
  class BlackJack
    
    def initialize
      @player = 0
      @dealer = 0
    end

    def deal
      return rand((2..10))
    end

    def begin
      @player += deal
      @dealer += deal
      puts "Let's Begin! Opening Scores:"
      output_scores
      player_play
    end
    
    def output_scores
      puts "Player: #{@player} | Dealer: #{@dealer} \n\n"
    end

    def player_play
      puts "Would you like another number? Y/N"
      new_deal = $stdin.gets.chomp.upcase

      if new_deal == 'Y' 
         num = deal
         puts "You get a #{num}."
         @player += num
         output_scores
         @player > 21 ? end_game('player') : player_play
      elsif new_deal == 'N'
        dealer_play
      else
        puts "Please enter Y / N"
        player_play
      end
    end

    def dealer_play
      while @dealer <= 16
        num = deal
        puts "Dealer gets #{num}"
        @dealer += num
        output_scores
      end

      @dealer > 21 ? end_game('dealer') : end_game
    end
    
    def end_game(loser = nil)
      if loser.nil?
        puts "Game Over!"
        puts "### #{@player > @dealer ? "You Win!" : "Dealer Wins!"} ###"
      elsif loser == 'player'
        puts "You break 21!"
        puts "### You lose! ###"
      else
        puts "Dealer breaks 21!"
        puts "### Dealer loses! ###"
      end
    end
  end

  game = BlackJack.new()
  game.begin
  
{% endhighlight %}


