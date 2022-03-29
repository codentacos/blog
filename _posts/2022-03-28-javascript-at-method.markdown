---
layout: post
title:  "Reverse Indexing With JavaScript's .at() Method"
date:   2022-03-28 16:27:00 -0600
categories: [javascript]
---
With ES2022, the `.at()` method was added to the JavaScript langauge which has finally granted the ability to do reverse indexing which is available natively in some other languages such as Python. Reverse indexing refers to the ability to access indexes in a string or array using negative index numbers. Previously in JavaScript this had to be done as follows:

{% highlight javascript %}
// Arrays
const nums = [1,2,3,4];

nums.slice(-1)[0] // 4
nums[nums.length - 2] // 3

// Strings
const str = 'Hello World!';

str.slice(-6, -5) // W
str[str.length - 6] // W
{% endhighlight %}

With the addition of `.at()` the syntax for negative indexing can be simplified as seen below to allow more readable code.

{% highlight javascript %}
// Arrays
const nums = [1,2,3,4];

nums.at(-1) // 4

// Strings
const str = 'Hello World!';

str.at(-6, -5) // W
{% endhighlight %}