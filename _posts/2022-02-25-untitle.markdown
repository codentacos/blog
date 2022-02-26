---
layout: post
title:  "Linear Search VS Binary Search"
date:   2022-02-25 23:27:00 -0600
categories: [algorithms]
---
Pretty often as developers we find ourselves needing to search through arrays for specific values. More times than not a simple for loop is enough to get the job done. Say we wanted to write a function to do this. Pretty simple, we just need an array and the number we are looking for. This is commonly known as a **Linear Search** and it's time complexity is **O(n)**.

{% highlight javascript %}
const data = Array.from(Array(10).keys());

const findVal = (nums, target) => {
  for (let i = 0; i < nums.length; i ++) {
      if (nums[i] === target) {
          return i;
      }
  }
    return -1;
}

// total max number of operations: 10
{% endhighlight %}

This is great for unsorted or smaller datasets and maybe even a few hundred or thousand items. What happens though if we need to search through millions or billions of items in a massive array? Provided we have a **sorted array** we can use **Binary Search**. (It wouldn't be faster to sort our data and then use Binary Search unfortunately because the fastest we can sort data is **O(n log n)**).

Let's look at an example of a massive array if we were to perform a Linear Search.

{% highlight javascript %}
const data = Array.from(Array(10000000).keys());

const findVal = (nums, target) => {
  for (let i = 0; i < nums.length; i ++) {
      if (nums[i] === target) {
          return i;
      }
  }
    return -1;
}

findVal(data, 35203);

// total number of operations to find result: 35,204
{% endhighlight %}

Linear Search took 35,204 operations to find our target. That's one operation for every element checked. This works but we can do better though. Let's find the same number in the same size dataset using Binary Search now.

{% highlight javascript %}
// Array with 10 million elements
const data = Array.from(Array(10000000).keys());

const findVal = (nums, target) => {
  let start = 0;
  let end = nums.length - 1;

  while (start <= end) {
    const mid = Math.floor(start + (end - start) / 2);

    if (mid === target) return mid;

    if (target < mid) {
      end = mid - 1;
    } else {
      start = mid + 1;
    }
  }
  return -1;
}

findVal(data, 35203);

// total number of operations to find result: 23
{% endhighlight %}

Now it has taken us only 23 operations to find the same value. This is clearly a substatial improvement over our Linear Search. The reason Binary Search is so effective is because with every iteration we eliminate half of our dataset so we no longer have to check every single element potentially. 