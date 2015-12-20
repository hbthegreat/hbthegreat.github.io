---
layout: post
title:  "Project Euler Solutions"
date:   2015-12-20 14:13:07
categories: programming
parent-category: Programming
parent-category-link: programming
---

<p>This post will focus on my solutions for Project Euler Problems.</p>
<p>At the time of writing this I had already completed 15+ challenges so I will add solutions to those in time when I get stuck on others.</p>
<p>The total amount of challenges I have solved on Project Euler can be seen in the following images:</p>
<div class="text-center"><img src="https://projecteuler.net/profile/Hbthegreat.png" /></div>
<b>DISCLAIMER: These solutions do actually contain the answers so if you are looking to complete them yourself do that before reading any further.</b>

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
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingThree">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
        Project Euler Problem 12 - Highly divisible triangular number
      </a>
    </h4>
  </div>
  <div id="collapseThree" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingThree">
    <div class="panel-body">
      <div class="problem-description">
        <p>The sequence of triangle numbers is generated by adding the natural numbers. So the 7<sup>th</sup> triangle number would be 1 + 2 + 3 + 4 + 5 + 6 + 7 = 28. The first ten terms would be:</p>
        <p class="text-center">1, 3, 6, 10, 15, 21, 28, 36, 45, 55, ...</p>
        <p>Let us list the factors of the first seven triangle numbers:</p>
        <blockquote><b>&nbsp;1</b>: 1<br>
          <b>&nbsp;3</b>: 1,3<br>
          <b>&nbsp;6</b>: 1,2,3,6<br>
          <b>10</b>: 1,2,5,10<br>
          <b>15</b>: 1,3,5,15<br>
          <b>21</b>: 1,3,7,21<br>
          <b>28</b>: 1,2,4,7,14,28
        </blockquote>
        <p>We can see that 28 is the first triangle number to have over five divisors.</p>
        <p>What is the value of the first triangle number to have over five hundred divisors?</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>Firstly we need to have a function that count the number of factors in essentially any input:</p>
{% highlight js %}
numberOfFactors(numberToTest)
{
  var totalFactors = 0;
  var limitOfFactors = Math.sqrt(numberToTest);
  for(var i = 1; i < limitOfFactors; i++)
  {
    if(numberToTest % i === 0) totalFactors+=2;
  }
  if(numberToTest/limitOfFactors === limitOfFactors) totalFactors++;
  return totalFactors;
}
{% endhighlight %}
      <p>Now that we can count the number of factors in a number we need to be able to check through every Triangle Number to find one that has more than 500 factors.</p>
{% highlight js %}
var currTriangle = 1;
var increment = 1;
var factors = 1;
while(factors <= 500)
{
  increment++;
  currTriangle += increment;
  factors = numberOfFactors(currTriangle);
}
console.log("The first triangle number with 500 or more factors is: "+ currTriangle);
{% endhighlight %}
      <p>After running our algorithm the with a list of triangular numbers we get the answer: 76576500.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFour">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseFour" aria-expanded="false" aria-controls="collapseFour">
        Project Euler Problem 13 - Large sum
      </a>
    </h4>
  </div>
  <div id="collapseFour" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFour">
    <div class="panel-body">
      <div class="problem-description">
        <p>Work out the first ten digits of the sum of the following one-hundred 50-digit numbers.</p>
        <div>
        37107287533902102798797998220837590246510135740250<br>
        46376937677490009712648124896970078050417018260538<br>
        74324986199524741059474233309513058123726617309629<br>
        91942213363574161572522430563301811072406154908250<br>
        23067588207539346171171980310421047513778063246676<br>
        89261670696623633820136378418383684178734361726757<br>
        28112879812849979408065481931592621691275889832738<br>
        44274228917432520321923589422876796487670272189318<br>
        47451445736001306439091167216856844588711603153276<br>
        70386486105843025439939619828917593665686757934951<br>
        62176457141856560629502157223196586755079324193331<br>
        64906352462741904929101432445813822663347944758178<br>
        92575867718337217661963751590579239728245598838407<br>
        58203565325359399008402633568948830189458628227828<br>
        80181199384826282014278194139940567587151170094390<br>
        35398664372827112653829987240784473053190104293586<br>
        86515506006295864861532075273371959191420517255829<br>
        71693888707715466499115593487603532921714970056938<br>
        54370070576826684624621495650076471787294438377604<br>
        53282654108756828443191190634694037855217779295145<br>
        36123272525000296071075082563815656710885258350721<br>
        45876576172410976447339110607218265236877223636045<br>
        17423706905851860660448207621209813287860733969412<br>
        81142660418086830619328460811191061556940512689692<br>
        51934325451728388641918047049293215058642563049483<br>
        62467221648435076201727918039944693004732956340691<br>
        15732444386908125794514089057706229429197107928209<br>
        55037687525678773091862540744969844508330393682126<br>
        18336384825330154686196124348767681297534375946515<br>
        80386287592878490201521685554828717201219257766954<br>
        78182833757993103614740356856449095527097864797581<br>
        16726320100436897842553539920931837441497806860984<br>
        48403098129077791799088218795327364475675590848030<br>
        87086987551392711854517078544161852424320693150332<br>
        59959406895756536782107074926966537676326235447210<br>
        69793950679652694742597709739166693763042633987085<br>
        41052684708299085211399427365734116182760315001271<br>
        65378607361501080857009149939512557028198746004375<br>
        35829035317434717326932123578154982629742552737307<br>
        94953759765105305946966067683156574377167401875275<br>
        88902802571733229619176668713819931811048770190271<br>
        25267680276078003013678680992525463401061632866526<br>
        36270218540497705585629946580636237993140746255962<br>
        24074486908231174977792365466257246923322810917141<br>
        91430288197103288597806669760892938638285025333403<br>
        34413065578016127815921815005561868836468420090470<br>
        23053081172816430487623791969842487255036638784583<br>
        11487696932154902810424020138335124462181441773470<br>
        63783299490636259666498587618221225225512486764533<br>
        67720186971698544312419572409913959008952310058822<br>
        95548255300263520781532296796249481641953868218774<br>
        76085327132285723110424803456124867697064507995236<br>
        37774242535411291684276865538926205024910326572967<br>
        23701913275725675285653248258265463092207058596522<br>
        29798860272258331913126375147341994889534765745501<br>
        18495701454879288984856827726077713721403798879715<br>
        38298203783031473527721580348144513491373226651381<br>
        34829543829199918180278916522431027392251122869539<br>
        40957953066405232632538044100059654939159879593635<br>
        29746152185502371307642255121183693803580388584903<br>
        41698116222072977186158236678424689157993532961922<br>
        62467957194401269043877107275048102390895523597457<br>
        23189706772547915061505504953922979530901129967519<br>
        86188088225875314529584099251203829009407770775672<br>
        11306739708304724483816533873502340845647058077308<br>
        82959174767140363198008187129011875491310547126581<br>
        97623331044818386269515456334926366572897563400500<br>
        42846280183517070527831839425882145521227251250327<br>
        55121603546981200581762165212827652751691296897789<br>
        32238195734329339946437501907836945765883352399886<br>
        75506164965184775180738168837861091527357929701337<br>
        62177842752192623401942399639168044983993173312731<br>
        32924185707147349566916674687634660915035914677504<br>
        99518671430235219628894890102423325116913619626622<br>
        73267460800591547471830798392868535206946944540724<br>
        76841822524674417161514036427982273348055556214818<br>
        97142617910342598647204516893989422179826088076852<br>
        87783646182799346313767754307809363333018982642090<br>
        10848802521674670883215120185883543223812876952786<br>
        71329612474782464538636993009049310363619763878039<br>
        62184073572399794223406235393808339651327408011116<br>
        66627891981488087797941876876144230030984490851411<br>
        60661826293682836764744779239180335110989069790714<br>
        85786944089552990653640447425576083659976645795096<br>
        66024396409905389607120198219976047599490197230297<br>
        64913982680032973156037120041377903785566085089252<br>
        16730939319872750275468906903707539413042652315011<br>
        94809377245048795150954100921645863754710598436791<br>
        78639167021187492431995700641917969777599028300699<br>
        15368713711936614952811305876380278410754449733078<br>
        40789923115535562561142322423255033685442488917353<br>
        44889911501440648020369068063960672322193204149535<br>
        41503128880339536053299340368006977710650566631954<br>
        81234880673210146739058568557934581403627822703280<br>
        82616570773948327592232845941706525094512325230608<br>
        22918802058777319719839450180888072429661980811197<br>
        77158542502016545090413245809786882778948721859617<br>
        72107838435069186155435662884062257473692284509516<br>
        20849603980134001723930671666823555245252804609722<br>
        53503534226472524250874054075591789781264330331690<br>
      </div>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>First thougths when looking at this problem are - "Holy %*#! thats a lot of numbers" we firstly need to store them in an array that can be used in our solution, in this case we will use strings because right now they are too long to use regular integer addition:</p>
{% highlight js %}
var strNums = ["37107287533902102798797998220837590246510135740250",
"46376937677490009712648124896970078050417018260538",
"74324986199524741059474233309513058123726617309629",
"91942213363574161572522430563301811072406154908250",
"23067588207539346171171980310421047513778063246676",
"89261670696623633820136378418383684178734361726757",
"28112879812849979408065481931592621691275889832738",
"44274228917432520321923589422876796487670272189318",
"47451445736001306439091167216856844588711603153276",
"70386486105843025439939619828917593665686757934951",
"62176457141856560629502157223196586755079324193331",
"64906352462741904929101432445813822663347944758178",
"92575867718337217661963751590579239728245598838407",
"58203565325359399008402633568948830189458628227828",
"80181199384826282014278194139940567587151170094390",
"35398664372827112653829987240784473053190104293586",
"86515506006295864861532075273371959191420517255829",
"71693888707715466499115593487603532921714970056938",
"54370070576826684624621495650076471787294438377604",
"53282654108756828443191190634694037855217779295145",
"36123272525000296071075082563815656710885258350721",
"45876576172410976447339110607218265236877223636045",
"17423706905851860660448207621209813287860733969412",
"81142660418086830619328460811191061556940512689692",
"51934325451728388641918047049293215058642563049483",
"62467221648435076201727918039944693004732956340691",
"15732444386908125794514089057706229429197107928209",
"55037687525678773091862540744969844508330393682126",
"18336384825330154686196124348767681297534375946515",
"80386287592878490201521685554828717201219257766954",
"78182833757993103614740356856449095527097864797581",
"16726320100436897842553539920931837441497806860984",
"48403098129077791799088218795327364475675590848030",
"87086987551392711854517078544161852424320693150332",
"59959406895756536782107074926966537676326235447210",
"69793950679652694742597709739166693763042633987085",
"41052684708299085211399427365734116182760315001271",
"65378607361501080857009149939512557028198746004375",
"35829035317434717326932123578154982629742552737307",
"94953759765105305946966067683156574377167401875275",
"88902802571733229619176668713819931811048770190271",
"25267680276078003013678680992525463401061632866526",
"36270218540497705585629946580636237993140746255962",
"24074486908231174977792365466257246923322810917141",
"91430288197103288597806669760892938638285025333403",
"34413065578016127815921815005561868836468420090470",
"23053081172816430487623791969842487255036638784583",
"11487696932154902810424020138335124462181441773470",
"63783299490636259666498587618221225225512486764533",
"67720186971698544312419572409913959008952310058822",
"95548255300263520781532296796249481641953868218774",
"76085327132285723110424803456124867697064507995236",
"37774242535411291684276865538926205024910326572967",
"23701913275725675285653248258265463092207058596522",
"29798860272258331913126375147341994889534765745501",
"18495701454879288984856827726077713721403798879715",
"38298203783031473527721580348144513491373226651381",
"34829543829199918180278916522431027392251122869539",
"40957953066405232632538044100059654939159879593635",
"29746152185502371307642255121183693803580388584903",
"41698116222072977186158236678424689157993532961922",
"62467957194401269043877107275048102390895523597457",
"23189706772547915061505504953922979530901129967519",
"86188088225875314529584099251203829009407770775672",
"11306739708304724483816533873502340845647058077308",
"82959174767140363198008187129011875491310547126581",
"97623331044818386269515456334926366572897563400500",
"42846280183517070527831839425882145521227251250327",
"55121603546981200581762165212827652751691296897789",
"32238195734329339946437501907836945765883352399886",
"75506164965184775180738168837861091527357929701337",
"62177842752192623401942399639168044983993173312731",
"32924185707147349566916674687634660915035914677504",
"99518671430235219628894890102423325116913619626622",
"73267460800591547471830798392868535206946944540724",
"76841822524674417161514036427982273348055556214818",
"97142617910342598647204516893989422179826088076852",
"87783646182799346313767754307809363333018982642090",
"10848802521674670883215120185883543223812876952786",
"71329612474782464538636993009049310363619763878039",
"62184073572399794223406235393808339651327408011116",
"66627891981488087797941876876144230030984490851411",
"60661826293682836764744779239180335110989069790714",
"85786944089552990653640447425576083659976645795096",
"66024396409905389607120198219976047599490197230297",
"64913982680032973156037120041377903785566085089252",
"16730939319872750275468906903707539413042652315011",
"94809377245048795150954100921645863754710598436791",
"78639167021187492431995700641917969777599028300699",
"15368713711936614952811305876380278410754449733078",
"40789923115535562561142322423255033685442488917353",
"44889911501440648020369068063960672322193204149535",
"41503128880339536053299340368006977710650566631954",
"81234880673210146739058568557934581403627822703280",
"82616570773948327592232845941706525094512325230608",
"22918802058777319719839450180888072429661980811197",
"77158542502016545090413245809786882778948721859617",
"72107838435069186155435662884062257473692284509516",
"20849603980134001723930671666823555245252804609722",
"53503534226472524250874054075591789781264330331690"];
{% endhighlight %}
      <p>Now we need to have a function that allows us to use addition on the strings of 50+ digit numbers.</p>
{% highlight js %}
function sumStrings(firstNum,secondNum)
{
  firstNum = firstNum.split("").reverse();
  secondNum = secondNum.split("").reverse();

  var sum = [];
  var carryDigit = 0;
  var totalLength = Math.max(firstNum.length,secondNum.length) + 1;
  for(var i = 0; i < totalLength; i++)
  {
    var temp = carryDigit;
    if(firstNum.length > i) temp+= parseInt(firstNum[i]);
    if(secondNum.length > i) temp+= parseInt(secondNum[i]);
    sum.push(temp % 10);
    carryDigit = Math.floor(temp/10);
  }
  while(sum[sum.length-1] === 0) sum.pop();
  return sum.reverse().join("");
}
{% endhighlight %}
      <p>We can then use our newly created function to process the entire list of huge numbers provided above:</p>
{% highlight js %}
/*Set the initial string value to 0*/
var sum = "0";

for(i in strNums)
{
  sum = sumStrings(sum,strNums[i]);
}

console.log("The first 10 digits of the sum of all the numbers provided is: "+ sum.substr(0,10));
{% endhighlight %}
      <p>After running our algorithm the with a list of triangular numbers we get the answer: 5537376230.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFive">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseFive" aria-expanded="false" aria-controls="collapseFive">
        Project Euler Problem 14 - Longest Collatz sequence
      </a>
    </h4>
  </div>
  <div id="collapseFive" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFive">
    <div class="panel-body">
      <div class="problem-description">
        <p>The following iterative sequence is defined for the set of positive integers:</p>
        <p style="margin-left:50px;"><var>n</var> → <var>n</var>/2 (<var>n</var> is even)<br><var>n</var> → 3<var>n</var> + 1 (<var>n</var> is odd)</p>
        <p>Using the rule above and starting with 13, we generate the following sequence:</p>
        <div class="text-center">13 → 40 → 20 → 10 → 5 → 16 → 8 → 4 → 2 → 1</div>
        <p>It can be seen that this sequence (starting at 13 and finishing at 1) contains 10 terms. Although it has not been proved yet (Collatz Problem), it is thought that all starting numbers finish at 1.</p>
        <p>Which starting number, under one million, produces the longest chain?</p>
        <p class="note"><b>NOTE:</b> Once the chain starts the terms are allowed to go above one million.</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
      <p>My first thought when looking at this problem is that it seems a bit more straight forward than other problems we have solved today and should only take a simple algorithm.</p>
{% highlight js %}
/*The current number being test "current longest chain candidated"*/
var clcc = 1;
/*Length of the current chain*/
var loc = 1;

for(var i = 2; i < 1000000; i++)
{
  var temp = i;
  var count = 0;
  while(temp != 1)
  {
    if (temp % 2 == 0) temp = temp/2;
    else temp = temp*3 + 1;
    count++;
  }
  if(count > loc)
  {
    loc = count;
    clcc = i;
  }
}

console.log("The longest chain with a number starting under 1 million is: "+loc+ " that chain belongs to the number: "+clcc);
{% endhighlight %}
      <p>After running this seemingly inefficient algorithm I got "The longest chain with a number starting under 1 million is: 524 that chain belongs to the number: 837799". So our answer is 837799.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSix">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseSix" aria-expanded="false" aria-controls="collapseSix">
        Project Euler Problem 18 - Maximum path sum I
      </a>
    </h4>
  </div>
  <div id="collapseSix" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSix">
    <div class="panel-body">
      <div class="problem-description">
        <p>By starting at the top of the triangle below and moving to adjacent numbers on the row below, the maximum total from top to bottom is 23.</p>
        <p class="text-center"><span style="color:#ff0000;"><b>3</b></span><br><span style="color:#ff0000;"><b>7</b></span> 4<br>
        2 <span style="color:#ff0000;"><b>4</b></span> 6<br>
        8 5 <span style="color:#ff0000;"><b>9</b></span> 3</p>
        <p>That is, 3 + 7 + 4 + 9 = 23.</p>
        <p>Find the maximum total from top to bottom of the triangle below:</p>
        <p class="text-center">75<br>
        95 64<br>
        17 47 82<br>
        18 35 87 10<br>
        20 04 82 47 65<br>
        19 01 23 75 03 34<br>
        88 02 77 73 07 63 67<br>
        99 65 04 28 06 16 70 92<br>
        41 41 26 56 83 40 80 70 33<br>
        41 48 72 33 47 32 37 16 94 29<br>
        53 71 44 65 25 43 91 52 97 51 14<br>
        70 11 33 28 77 73 17 78 39 68 17 57<br>
        91 71 52 38 17 14 91 43 58 50 27 29 48<br>
        63 66 04 68 89 53 67 30 73 16 69 87 40 31<br>
        04 62 98 27 23 09 70 98 73 93 38 53 60 04 23</p>
        <p class="note"><b>NOTE:</b> As there are only 16384 routes, it is possible to solve this problem by trying every route. However, <b>Problem 67</b>, is the same challenge with a triangle containing one-hundred rows; it cannot be solved by brute force, and requires a clever method! ;o)</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>The first thing I notice about this challenge is that it should be easily brute-forceable but for the sake of having code ready for Problem 67 I will not be brute forcing this challenge.</p>
        <p>We will start by putting the given triangle into a usable array.</p>
{% highlight js %}
var pyramid = [
        [75],
        [95,64],
        [17,47,82],
        [18,35,87,10],
        [20,04,82,47,65],
        [19,01,23,75,03,34],
        [88,02,77,73,07,63,67],
        [99,65,04,28,06,16,70,92],
        [41,41,26,56,83,40,80,70,33],
        [41,48,72,33,47,32,37,16,94,29],
        [53,71,44,65,25,43,91,52,97,51,14],
        [70,11,33,28,77,73,17,78,39,68,17,57],
        [91,71,52,38,17,14,91,43,58,50,27,29,48],
        [63,66,04,68,89,53,67,30,73,16,69,87,40,31],
        [04,62,98,27,23,09,70,98,73,93,38,53,60,04,23]
];
{% endhighlight %}
      <p>Now that our pyramid is properly created in code we can begin to find the best path through the pyramid to get the highest sum!</p>
{% highlight js %}
var maxSum = 0;
for(var i = 0; i < 1000; i++)
{
  var sum = 0;
  var lastIndex = 0;
  for(var level in pyramid)
  {
    if(level == 0)
    {
        sum = 75;
        lastIndex = 0;
    }
    else
    {
        var options = pyramid[level];
        var total = options[lastIndex] + options[lastIndex + 1];
        var choice = Math.random() * total;
        lastIndex = (choice <= options[lastIndex] ? lastIndex : lastIndex + 1);
        sum += options[lastIndex];
    }
  }
  maxSum = Math.max(maxSum, sum);
}
console.log("The maximum path available through the pyramid is: "+ maxSum);
{% endhighlight %}
      <p>After running this algorithm we can find that the maximum path through the pyramid is 1074.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSeven">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseSeven" aria-expanded="false" aria-controls="collapseSeven">
          Project Euler Problem 19 - Counting Sundays
      </a>
    </h4>
  </div>
  <div id="collapseSeven" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSeven">
    <div class="panel-body">
      <div class="problem-description">
        <p>You are given the following information, but you may prefer to do some research for yourself.</p>
        <ul>
          <li>1 Jan 1900 was a Monday.</li>
          <li>Thirty days has September,<br>
              April, June and November.<br>
              All the rest have thirty-one,<br>
              Saving February alone,<br>
              Which has twenty-eight, rain or shine.<br>
              And on leap years, twenty-nine.</li>
          <li>A leap year occurs on any year evenly divisible by 4, but not on a century unless it is divisible by 400.</li>
        </ul>
        <p>How many Sundays fell on the first of the month during the twentieth century (1 Jan 1901 to 31 Dec 2000)?</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>This problem could be solvable purely by pulling out a calendar and counting every single Sunday... but we won't be doing that we will be actually calculating the amount of Sundays!</p>
        <p>We can use JavaScript's Date functions to our advantage in this excercise.</p>
{% highlight js %}
/*We will initialise the date to 1st of Jan 1901*/
var currentDate = new Date("1 Jan 1901");
/*The final date in our range*/
var endDate = new Date("31 Dec 2000");
var numOfSundays = 0;

while(currentDate <= endDate)
{
  /*getDay = 0 returns true if it is a Sunday. getDate() == 1 returns true if it is on the first of the month*/
  if(currentDate.getDay() == 0 && currentDate.getDate() == 1) numOfSundays++;
  currentDate.setDate(currentDate.getDate()+1);
}

console.log("The number of sundays during the period was:" + numOfSundays);
{% endhighlight %}
      <p>After iterating over all the dates in the the range specified we get to the answer of 171 Sundays!</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingEight">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseEight" aria-expanded="false" aria-controls="collapseEight">
        Project Euler Problem 21 - Amicable numbers
      </a>
    </h4>
  </div>
  <div id="collapseEight" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingEight">
    <div class="panel-body">
      <div class="problem-description">
        <p>Let d(<i>n</i>) be defined as the sum of proper divisors of <i>n</i> (numbers less than <i>n</i> which divide evenly into <i>n</i>).<br>
        If d(<i>a</i>) = <i>b</i> and d(<i>b</i>) = <i>a</i>, where <i>a</i> ≠ <i>b</i>, then <i>a</i> and <i>b</i> are an amicable pair and each of <i>a</i> and <i>b</i> are called amicable numbers.</p>
        <p>For example, the proper divisors of 220 are 1, 2, 4, 5, 10, 11, 20, 22, 44, 55 and 110; therefore d(220) = 284. The proper divisors of 284 are 1, 2, 4, 71 and 142; so d(284) = 220.</p>
        <p>Evaluate the sum of all the amicable numbers under 10000.</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>To start with solving this problem we will need a way to see if a particular number is Amicable. So let's put together a function that does that first.</p>
        <p>After initially looking at the problem I discovered I also had to write functions for getting factors and summing them so they are also included.</p>
{% highlight js %}
function getFactors(number)
{
  /*returns 0 if number is 0 or 1 if it is 1/2/3 as the only factor is 1*/
  if(number <= 3)
  {
    switch(number)
    {
      case 0:
      return [0];
      default:
      return [1];
    }
  }
  /*all numbers have 1 as a factor*/
  var factors = [1];
  var factorLimit = Math.floor(Math.sqrt(number));
  for(var i = 2; i < factorLimit; i++)
  {
    if (number % i === 0)
    {
      /*adds both factors found at the same time*/
      factors.push(i);
      factors.push(number/i);
    }
  }
  if(number/factorLimit == factorLimit) factors.push(factorLimit);
  else if (number % factorLimit === 0)
  {
    factors.push(factorLimit);
    factors.push(number/factorLimit);
  }
  return factors;
}

function arraySum(numericalArray)
{
  var sum = 0;
  for(var i in numericalArray)
  {
    sum += numericalArray[i];
  }
  return sum;
}

function sumOfFactors(number)
{
  return arraySum(getFactors(number));
}

function isAmicable(number)
{
  var pair = sumOfFactors(number);
  if (pair == number) return false;
  if(sumOfFactors(pair) == number) return true;
  else return false;
}
{% endhighlight js %}

<p>Now that we have all the tools we need to test for Amicable numbers all thats left is to get the sum of all of them below 10000 as started in the question description.</p>

{% highlight js %}
var sum = 0;
for(var i = 2; i < 10000; i++)
{
  if(isAmicable(i)) sum+=i;
}
console.log("The sum of all Amicable numbers below 10000: " + sum);
{% endhighlight %}

      <p>From this we can establish that the sumof all Amicable numbers below 10000 is 31626.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingNine">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseNine" aria-expanded="false" aria-controls="collapseNine">
        Project Euler Problem 23 - Non-abundant sums
      </a>
    </h4>
  </div>
  <div id="collapseNine" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingNine">
    <div class="panel-body">
      <div class="problem-description">
        <p>A perfect number is a number for which the sum of its proper divisors is exactly equal to the number. For example, the sum of the proper divisors of 28 would be 1 + 2 + 4 + 7 + 14 = 28, which means that 28 is a perfect number.</p>
        <p>A number <var>n</var> is called deficient if the sum of its proper divisors is less than <var>n</var> and it is called abundant if this sum exceeds <var>n</var>.</p>
        <p>As 12 is the smallest abundant number, 1 + 2 + 3 + 4 + 6 = 16, the smallest number that can be written as the sum of two abundant numbers is 24. By mathematical analysis, it can be shown that all integers greater than 28123 can be written as the sum of two abundant numbers. However, this upper limit cannot be reduced any further by analysis even though it is known that the greatest number that cannot be expressed as the sum of two abundant numbers is less than this limit.</p>
        <p>Find the sum of all the positive integers which cannot be written as the sum of two abundant numbers.</p>
      </div>
      <div class="solution">
        <p>For this challenge I have decided to do it in <b>JavaScript</b>.</p>
        <p>First things first. Let's create a function that checks if a number is Abundant according to the rules listed above.</p>
{% highlight js %}
function isAbundant(number)
{
  /*we can reuse our sumOfFactors from problem 21 to help us here*/
  return (sumOfFactors(number) > number);
}
{% endhighlight %}
      <p>Once we have tested if a number is abundant we need to find all abundant numbers below 28123.</p>
{% highlight js %}
var abundants = [];
var maximum = 28123;

for(var i = 1; i <= maximum; i++)
{
  abundants[i] = isAbundant(i);
}
{% endhighlight %}
<p>Now that we have a list of abundants below 28123 we can test summing 2 abundant numbers together to get positive integers. Once we have these we can get the total sum.</p>
{% highlight js %}
function testSum(number)
{
  var testLimit = Math.floor(number/2);
  for(var i in abundants)
  {
    if(i > testLimit) return false;
    if(abundants[i] && abundants[number-i]) return true;
  }
  return false;
}
var sum = maximum * (maximum + 1) / 2; //sum of all integers

for(var i in abundants)
{
  if(testSum(i)) sum -= i;
}

console.log("The sum of all positive integers which cannot be written as the sum of 2 abundants under 28123 is: " + sum);
{% endhighlight %}
      <p>Once this set of functions eventually evaluates we get the answer of: 4179871.</p>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingTen">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseTen" aria-expanded="false" aria-controls="collapseTen">
        Project Euler Problem 24 - Lexicographic permutations
      </a>
    </h4>
  </div>
  <div id="collapseTen" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTen">
    <div class="panel-body">
      <div class="problem-description">
        <p>A permutation is an ordered arrangement of objects. For example, 3124 is one possible permutation of the digits 1, 2, 3 and 4. If all of the permutations are listed numerically or alphabetically, we call it lexicographic order. The lexicographic permutations of 0, 1 and 2 are:</p>
        <p class="text-center">012&nbsp; &nbsp;021&nbsp; &nbsp;102&nbsp; &nbsp;120&nbsp; &nbsp;201&nbsp; &nbsp;210</p>
        <p>What is the millionth lexicographic permutation of the digits 0, 1, 2, 3, 4, 5, 6, 7, 8 and 9?</p>
      </div>
      <div class="solution">
        <p>When approaching this problem is is easy to see that we need a function that can take a string/list of numbers and generate lexographic permutations. So we will start there.</p>
{% highlight js %}
var tempPerm = "0123456789".split("");
function lexographicPermutation(str)
{
  var swap = function(firstCharacter, secondCharacter)
  {
    var temp = str[firstCharacter];
    str[firstCharacter] = str[secondCharacter];
    str[secondCharacter] = temp;
  }
  var k = -1;
  //Here we are finding the least significant pair of numbers
  //that meet the criteria of a permutation
  for(var i = 0; i < str.length -1; i++)
  {
    if (str[i] < str[i+1]) k = i;
  }

  if(k ==-1)return str; //This means there are no more permutations

  var l = -1;
  for(var i = 0; i < str.length; i++)
  {
    if(str[k] < str[i]) l=i;
  }
  //now we must swap k and l to create the next permutation
  swap(k,l);

  //most of the string is already in the correct order as we are only adjusting
  //2 chars at a time. So we must reverse the sequence for k+1 length in the string an
  //add it back to the end
  return str.slice(0, k+1).concat(str.slice(k+1).reverse());
}
{% endhighlight %}
      <p>Now that we have a function that takes a string input and returns a lexographic permutation of that string we can complete the problem.</p>
{% highlight js %}
for(var i = 1; i < 1000000; i++)
{
  //we will use tempPerm from above
  tempPerm = lexographicPermutation(tempPerm);
}

console.log("The one millionth permutation of 0123456789 is: " + tempPerm.join(""));
{% endhighlight %}

      </div>
    </div>
  </div>
</div>
