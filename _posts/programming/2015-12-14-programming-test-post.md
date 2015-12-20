---
layout: post
title:  "Project Euler Solutions"
date:   2015-12-20 14:13:07
categories: programming
parent-category: Programming
parent-category-link: programming
---

This post will focus my solutions for Project Euler Problems.
At the time of writing this I had already completed 15+ challenges so I will add solutions to those in time

<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingOne">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseOne" aria-expanded="false" aria-controls="collapseOne">
        Project Euler Problem 10
      </a>
    </h4>
  </div>
  <div id="collapseOne" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingOne">
    <div class="panel-body">
      <div class="problem-description">
        <p>The sum of the primes below 10 is 2 + 3 + 5 + 7 = 17.</p>
        <p>Find the sum of all the primes below two million.</p
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>The first thing I think about when seeing this problem is "what is the correct way to tell a computer that it has found a prime?" to do that we must first understand what makes a number prime.</p>
        <p>An integer is prime if it is not divisible by any prime numbers less than or equal to its square root.</p>
        {% highlight js %}
        function isPrime(number)
        {
          if(number < 2) return false;

          var sqrtNumber = Math.floor(Math.sqrt(number));

          for(var i = 2; i <= sqrtNumber; i++)
          {
            if(number % i === 0)
            {
              return false;
            }
          }
          return true;
        }
        {% endhighlight %}
        <p>Using this function we can essentially brute-force all the primes below 2 million and add them all together. This may not be the most elegant solution but it gets the job done.</p>
        {% highlight js %}
        function sumAllPrimesUnderN(num)
        {
          var total = 0;
          for(var i = 0; i<num; i++)
          {
            if(isPrime(i))
            {
              total = total+i;
            }
          }
          return total;
        }
        {% endhighlight %}
        <p>Then running the command:</p>
        {% highlight js %}
        sumAllPrimesUnderN(2000000);
        {% endhighlight%}
        <p>We get the answer: 142913828922</p>
        <p>
      </div>
    </div>
  </div>
</div>
