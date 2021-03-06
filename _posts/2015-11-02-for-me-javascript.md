---
layout: post
title: "All i have to do is learn Javascript"
date: 2015-11-01 13:00:00
categories: tungns
featured_image: /images/cover.jpg
---
Breaking or continuing loop in functional programming

## A common requirement of iteration is cancelation. Using for loops we can break to end iteration early.

{% highlight javascript %} 
const a = [0, 1, 2, 3, 4];
for (var i = 0; i < a.length; i++) {
  if (a[i] === 2) {
    break; // stop the loop
  }
  console.log(a[i]);
}
//> 0, 1

{% endhighlight javascript %} 

Another common requirement is to close over our variables.
A quick approach is to use .forEach but then we lack the ability to break. In this situation the closest we get is continue functionality through return.<br/>

{% highlight javascript %} 
[0, 1, 2, 3, 4].forEach(function(val, i) {
  if (val === 2) {
    // how do we stop?
    return true;
  }
  console.log(val); // your code
});
//> 0, 1, 3, 4

{% endhighlight javascript %} 

The .some is a method on Array prototype. It tests whether some element in the array passes the test implemented by the provided function. If any value is returning true, then it stops executing. Here is a MDN link for more details.
An example quoted from that link

{% highlight javascript %} 
const isBiggerThan10 = numb => numb > 10;

[2, 5, 8, 1, 4].some(isBiggerThan10);  // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
Using .some we get iteration functionally similar to .forEach but with the ability to break through return instead.
[0, 1, 2, 3, 4].some(function(val, i) {
  if (val === 2) {
    return true;
  }
  console.log(val); // your code
});
//> 0, 1

{% endhighlight javascript %} 

You keep returning false to make it continue to next item. When you return true, the loop will break and a.some(..) will return true.

{% highlight javascript %} 
// Array contains 2
const isTwoPresent = [0, 1, 2, 3, 4].some(function(val, i) {
  if (val === 2) {
    return true; // break
  }
});
console.log(isTwoPresent);
//> true

{% endhighlight javascript %} 


## Are you finish : continue :D

Getting array items from behind to front
If you want to get the array items from behind to front, just do this:

{% highlight javascript %} 
var newArray = [1, 2, 3, 4];

console.log(newArray.slice(-1)); // [4]
console.log(newArray.slice(-2)); // [3, 4]
console.log(newArray.slice(-3)); // [2, 3, 4]
console.log(newArray.slice(-4)); // [1, 2, 3, 4]

{% endhighlight javascript %} 

Short-circuits conditionals
If you have to execute a function just if a condition is true, like this:

{% highlight javascript %} 

if(condition){
    dosomething();
}
{% endhighlight javascript %} 

You can use a short-circuit just like this:

`condition && dosomething();`

Set variable default values using “||”
If you have to set a default value to variables, you can simple do this:

{% highlight javascript %} 

var a;

console.log(a); //undefined

a = a || 'default value';

console.log(a); //default value

a = a || 'new value';

console.log(a); //default value

{% endhighlight javascript %} 
