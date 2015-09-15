---
layout: post
title:  "The Name Game - Php"
date:   2015-05-11 19:02:10
tags: code-exercise php
---

[http://www.reddit.com/r/dailyprogrammer/the-name-game][link1]


Name Game in Php


**input:**
&nbsp;&nbsp;&nbsp;&nbsp; *Lincoln*
**output:**
&nbsp;&nbsp;&nbsp;&nbsp;Lincoln, Lincoln bo Bincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Bonana fanna fo Fincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Fee fy mo Mincoln,
&nbsp;&nbsp;&nbsp;&nbsp;Lincoln!

To test all cases use: *`Anna, Dave, Bob, Fred, Mary`*

~~~php

<?php

class rhyme
{
  // Find the first letter
  // Create the filler words
  // generate output

  public $name;
  private $letters = array();
  private $rhymeNames = array();
  private $firstLetter;


  /**
   * Constructor
   * Initialises variables
   * @return void
   * @input $name, string
   * @author pat
   **/
  function __construct($name)
  {
    $this->name = $name;
    $this->letters = array('B','F','M');
    $this->firstLetter = substr($name,0,1);
    $this->setRhymeNames();
  }

  /**
  * setRhymeNames
  *
  * sets the name replacements for each letter
  * @return void
  * @author pat
  **/
  private function setRhymeNames()
  {
    for( $i = 0; $i < count($this->letters); $i++ )
    {
      $this->rhymeNames[] = $this->rhymeName($this->letters[$i]);
    }
  }

  /**
   * RhymeName
   * Returns Rhmye name for an individual letter
   * @return string, name with first letter replaced to produce rhyme name
   * @author pat
   **/
  private function rhymeName($letter)
  {
    $fl = strtoupper($this->firstLetter);

    // If the name starts with a vowel lowercase the first letter, else remove it.
    $namePartial = ( preg_match('/^[AEIOU]$/', $fl) ) ? strtolower($this->name) : substr($this->name,1);
    return ($fl == $letter) ? $letter.'o-'.$namePartial : strtolower($letter).'o '.$letter . $namePartial;
  }

  /**
   * outPutRhyme
   * Outputs rhyme
   * @return null
   * @author pat
   **/
  public function outputRhyme()
  {
    $output = $this->name . ', ' . '<br>' .
              $this->name . ' ' .$this->rhymeNames[0] . ', '. '<br>' .
              'Bonana ' .'fanna ' .$this->rhymeNames[1] . ', ' . '<br>' .
              'Fee fy '. $this->rhymeNames[2] . '!<br>';

    echo $output;
  }

}

$rhyme = new Rhyme($_GET['name']);
$rhyme->outputRhyme();


~~~



[link1]: http://www.reddit.com/r/dailyprogrammer/comments/338p28/20150420_challenge_211_easy_the_name_game/

