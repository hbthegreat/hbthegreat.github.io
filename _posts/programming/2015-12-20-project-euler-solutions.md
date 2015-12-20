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
        Project Euler Problem 10 - Summation of Primes
      </a>
    </h4>
  </div>
  <div id="collapseOne" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingOne">
    <div class="panel-body">
      <div class="problem-description">
        <p>The sum of the primes below 10 is 2 + 3 + 5 + 7 = 17.</p>
        <p>Find the sum of all the primes below two million.</p>
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
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingTwo">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
        Project Euler Problem 11 - Largest Product in a Grid
      </a>
    </h4>
  </div>
  <div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
    <div class="panel-body">
      <div class="problem-description">
        <p>In the 20×20 grid below, four numbers along a diagonal line have been marked in red.</p>
            08 02 22 97 38 15 00 40 00 75 04 05 07 78 52 12 50 77 91 08<br>
            49 49 99 40 17 81 18 57 60 87 17 40 98 43 69 48 04 56 62 00<br>
            81 49 31 73 55 79 14 29 93 71 40 67 53 88 30 03 49 13 36 65<br>
            52 70 95 23 04 60 11 42 69 24 68 56 01 32 56 71 37 02 36 91<br>
            22 31 16 71 51 67 63 89 41 92 36 54 22 40 40 28 66 33 13 80<br>
            24 47 32 60 99 03 45 02 44 75 33 53 78 36 84 20 35 17 12 50<br>
            32 98 81 28 64 23 67 10 <span style="color:#ff0000;"><b>26</b></span> 38 40 67 59 54 70 66 18 38 64 70<br>
            67 26 20 68 02 62 12 20 95 <span style="color:#ff0000;"><b>63</b></span> 94 39 63 08 40 91 66 49 94 21<br>
            24 55 58 05 66 73 99 26 97 17 <span style="color:#ff0000;"><b>78</b></span> 78 96 83 14 88 34 89 63 72<br>
            21 36 23 09 75 00 76 44 20 45 35 <span style="color:#ff0000;"><b>14</b></span> 00 61 33 97 34 31 33 95<br>
            78 17 53 28 22 75 31 67 15 94 03 80 04 62 16 14 09 53 56 92<br>
            16 39 05 42 96 35 31 47 55 58 88 24 00 17 54 24 36 29 85 57<br>
            86 56 00 48 35 71 89 07 05 44 44 37 44 60 21 58 51 54 17 58<br>
            19 80 81 68 05 94 47 69 28 73 92 13 86 52 17 77 04 89 55 40<br>
            04 52 08 83 97 35 99 16 07 97 57 32 16 26 26 79 33 27 98 66<br>
            88 36 68 87 57 62 20 72 03 46 33 67 46 55 12 32 63 93 53 69<br>
            04 42 16 73 38 25 39 11 24 94 72 18 08 46 29 32 40 62 76 36<br>
            20 69 36 41 72 30 23 88 34 62 99 69 82 67 59 85 74 04 36 16<br>
            20 73 35 29 78 31 90 01 74 31 49 71 48 86 81 16 23 57 05 54<br>
            01 70 54 71 83 51 54 69 16 92 33 48 61 43 52 01 89 19 67 48<br>
        </p>
      </div>
      <div class="solution">
        <br>
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>Looking at this challenge we need to break the list of numbers down into a list/array structure for processing. I went with the option of manually breaking it down as it seemed faster than a coded solution: </p>
{% highlight js %}
var grid = [[08,02,22,97,38,15,00,40,00,75,04,05,07,78,52,12,50,77,91,08],
[49,49,99,40,17,81,18,57,60,87,17,40,98,43,69,48,04,56,62,00],
[81,49,31,73,55,79,14,29,93,71,40,67,53,88,30,03,49,13,36,65],
[52,70,95,23,04,60,11,42,69,24,68,56,01,32,56,71,37,02,36,91],
[22,31,16,71,51,67,63,89,41,92,36,54,22,40,40,28,66,33,13,80],
[24,47,32,60,99,03,45,02,44,75,33,53,78,36,84,20,35,17,12,50],
[32,98,81,28,64,23,67,10,26,38,40,67,59,54,70,66,18,38,64,70],
[67,26,20,68,02,62,12,20,95,63,94,39,63,08,40,91,66,49,94,21],
[24,55,58,05,66,73,99,26,97,17,78,78,96,83,14,88,34,89,63,72],
[21,36,23,09,75,00,76,44,20,45,35,14,00,61,33,97,34,31,33,95],
[78,17,53,28,22,75,31,67,15,94,03,80,04,62,16,14,09,53,56,92],
[16,39,05,42,96,35,31,47,55,58,88,24,00,17,54,24,36,29,85,57],
[86,56,00,48,35,71,89,07,05,44,44,37,44,60,21,58,51,54,17,58],
[19,80,81,68,05,94,47,69,28,73,92,13,86,52,17,77,04,89,55,40],
[04,52,08,83,97,35,99,16,07,97,57,32,16,26,26,79,33,27,98,66],
[88,36,68,87,57,62,20,72,03,46,33,67,46,55,12,32,63,93,53,69],
[04,42,16,73,38,25,39,11,24,94,72,18,08,46,29,32,40,62,76,36],
[20,69,36,41,72,30,23,88,34,62,99,69,82,67,59,85,74,04,36,16],
[20,73,35,29,78,31,90,01,74,31,49,71,48,86,81,16,23,57,05,54],
[01,70,54,71,83,51,54,69,16,92,33,48,61,43,52,01,89,19,67,48]];
{% endhighlight %}
        <p>Now that we have everything in a grid understood by javascript we can work on trying to find the lasgest product! We can take advantage of JavaScript's Math.max() function.</p>
{% highlight js %}
var highestProduct = 0;
var cellsToTest = 4;
for(var i = cellsToTest - 1; i < (grid.length - cellsToTest); i++)
{
  for(var k = cellsToTest - 1; k < (grid.length - cellsToTest); k++)
  {
    /*Checks if the current highestProduct is higher than the product of each minigrid. Updates if it finds a higher minigrid*/
    highestProduct = Math.max(highestProduct,

      /*Top Row*/
      /*Top Left*/
      (grid[i - 3][k - 3]*grid[i - 2][k - 2]*grid[i - 1][k - 1]*grid[i][k]),
      /*Top Middle*/
      (grid[i - 3][k]*grid[i - 2][k]*grid[i - 1][k]*grid[i][k]),
      /*Top Right*/
      (grid[i - 3][k + 3]*grid[i - 2][k + 2]*grid[i - 1][k + 1]*grid[i][k]),

      /*Middle Row*/
      /*Left Middle*/
      (grid[i][k - 3]*grid[i][k - 2]*grid[i][k - 1]*grid[i][k]),
      /*Right Middle*/
      (grid[i][k + 3]*grid[i][k + 2]*grid[i][k + 1]*grid[i][k]),

      /*Bottom Row*/
      /*Bottom Left*/
      (grid[i + 3][k - 3]*grid[i + 2][k - 2]*grid[i + 1][k + 1]*grid[i][k]),
      /*Bottom Middle*/
      (grid[i + 3][k]*grid[i + 2][k]*grid[i + 1][k]*grid[i][k]),
      /*Bottom Right*/
      (grid[i + 3][k + 3]*grid[i + 2][k + 2]*grid[i + 1][k + 1]*grid[i][k])
    )
  }
}
console.log('The highest product in the grid is: ' + highestProduct);
{% endhighlight%}
        <p>After running our grid through the algorithm we get the answer: 70600674.</p>
      </div>
    </div>
  </div>
</div>
