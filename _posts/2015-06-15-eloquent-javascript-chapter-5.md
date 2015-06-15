---
layout: post
title:  "Eloquent Javascript - Higher Order Functions"
date: 2015-06-15 12:24:10
tags: code js
---

####The Challenge
These are my solutions to problems in Eloquent Javascript Chapter 5 - Higher Order Functions. The full set of my solutions to this book are available on [my github account](https://github.com/pjho/eloquent-javascript).


> 
src [eloquentjavascript.net][src]

This block contains helper functions provided by the excercises. A json file is loaded with data containing the author's family tree. 

~~~ javascript

var chapter_5_excercises = function () { /* load json file */ }
var ancestry = JSON.parse(ANCESTRY_FILE);
// [ {"name": "Person Name", "sex": "m", "born": 1832, "died": 1905, "father": "F Name", "mother": "M Name"} ... ]

// Provided Helper Functions
function average(array) {
  function plus(a, b) { return a + b; }
  return (array.reduce(plus) / array.length).toFixed(2);
}

var byName = {};
ancestry.forEach(function(person) {
  byName[person.name] = person;
});
// End provided.

~~~

&nbsp;

#####Mother-child age difference
A fairly straight forward challenge using map and filter. This could have been improved by filtering out null values before mapping them.

~~~ javascript

  /*
  * Mother-child age difference
  *
  * Using the example data set from this chapter, compute the average age
  * difference between mothers and children (the age of the mother when the child
  * is born). You can use the average function defined earlier in this chapter.
  *
  * Note that not all the mothers mentioned in the data are themselves present in
  * the array. The byName object, which makes it easy to find a person’s object
  * from their name, might be useful here.
   ****/
  var motherAges = ancestry.map(function(person){
    mother = byName[person.mother];
    if (mother){
      return person.born - mother.born;
    }
  }).filter( function(item){return item; } );

  console.log(average(motherAges));
  // → 31.2222...

~~~

&nbsp;

#####Historical life expectancy
This challenge involved grouping the dataset and extracting mean values from the groups. In my approach I focussed too much on the values and not the grouping. As a result I added an extra step and created a redundant array of the values I needed which I then processed. The Autho's solution is below in the comments. His approach abstracts the grouping at a high level and focuses on the values when they're needed.

~~~ javascript

  /*
  * Historical life expectancy
  *
  * When we looked up all the people in our data set that lived more than 90 years,
  * only the latest generation in the data came out. Let’s take a closer look
  * at that phenomenon.
  *
  * Compute and output the average age of the people in the ancestry data set per
  * century. A person is assigned to a century by taking their year of death,
  * dividing it by 100, and rounding it up, as in Math.ceil(person.died / 100).
   ****/

  var centuries = ancestry.map( function(person) {
      return Math.ceil(person.died / 100);
    }).reduce(function(prev,current) {
      if( ! prev[current] ) prev[current] = [];
      return prev;
  },{});
    // console.log(centuries);

  var allCenturiesAges = ancestry.map( function(person){
    return [Math.ceil(person.died / 100), person.died - person.born];
  });
      // allCenturiesAges.forEach(function(el){console.log(el);});

  allCenturiesAges.forEach(function(item) {
    centuries[item[0]].push(item[1]);
  });

  output = "";
  for(var century in centuries) {
    output += century + ": " + average(centuries[century]) + " | ";
  }
  console.log(output)

  // function groupBy(array,callback) {}

  // → 16: 43.5 17: 51.2 18: 52.8 19: 54.8 20: 84.7 21: 94


/**************************
**** PROVIDED SOLUTION ****
// ************************
// This solution abstracts group by at a high level. In my approach I focused too
// much on getting the values I needed rather than grouping the people objects
// and using the data when I needed it.This is a much more DRY & reusable solution.
  function groupBy(array, groupOf) {
    var groups = {};
    array.forEach(function(element) {
      var groupName = groupOf(element);
      if (groupName in groups)
        groups[groupName].push(element);
      else
        groups[groupName] = [element];
    });
    return groups;
  }

  var byCentury = groupBy(ancestry, function(person) {
    return Math.ceil(person.died / 100);
  });

  for (var century in byCentury) {
    var ages = byCentury[century].map(function(person) {
      return person.died - person.born;
    });
    console.log(century + ": " + average(ages));
  }

***********************/
~~~

&nbsp;

~~~ javascript

  /*
  * Every and then some
  *
  * Arrays also come with the standard methods every and some. Both take a
  * predicate function that, when called with an array element as argument, returns
  * true or false. Just like && returns a true value only when the expressions on
  * both sides are true, every returns true only when the predicate returns true
  * for all elements of the array. Similarly, some returns true as soon as the
  * predicate returns true for any of the elements. They do not process more
  * elements than necessary—for example, if some finds that the predicate holds for
  * the first element of the array, it will not look at the values after that.
  *
  * Write two functions, every and some, that behave like these methods, except
  * that they take the array as their first argument rather than being a method.
   ****/

  function every(array,func) {
    for(var i = 0; i < array.length; i++) {
      if (!func(array[i])) return false;
    }
    return true;
  }

  function some(array,func) {
    for(var i = 0; i < array.length; i++) {
      if (func(array[i])) return true;
    }
    return false;
  }

  console.log(every([NaN, NaN, NaN], isNaN));
  // → true
  console.log(every([NaN, NaN, 4], isNaN));
  // → false
  console.log(some([NaN, 3, 4], isNaN));
  // → true
  console.log(some([2, 3, 4], isNaN));
  // → false
}

~~~

[src]: http://eloquentjavascript.net/05_higher_order.html
