---
layout: post
title:  "Math behind the discover mechanic in Hearthstone"
date:   2015-12-14 14:13:07
categories: gaming hearthstone
parent-category: Gaming
parent-category-link: gaming
---


<b>Disclaimer: This article will continue to grow as I spend more time exploring the mechanic.</b>

<p>The League of Explorers brought many new cards and dynamics to our beloved game Hearthstone and in my opinion the majority of the introduced cards have been both playable and add excitement to the game. This has been through new deck innovations and slight meta shifts which have been quite a welcome addition considering how stale the game can sometimes get during different parts of an expansion cycle. </p>

<p>I could write a lengthy article on each of the new cards but as others have already touched on most of those aspects I'd like to put the new mechanic Discover under a finer microscrope.</p>

<p>Before we deep dive head first into discover statistics it is important to understand the basic rules of the mechanic so that we can properly investigate the cards and their power levels.</p>
<p>Below are the rules and assumptions that need to be taken into account:</p>

* Discover presents you with 3 random options in most cases these are minions or spells. The only exceptions thus far are Sir Finley Mrgrglton that presents 3 options of basic hero powers that doesn't include your current hero power and Arch-Thief Rafaam that gives the option between his 3 powerful spells.
* The player must make a choice of one of the 3 options. It is not possible to "not" choose if you dislike the provided options.
* All 3 choices must be legal for your class. Neutral and Class minions and spells count as being legal.
* When a Discovery takes place Class cards are 4 times more likely to be presented as a choice than Neutral cards.
* Discovered cards are not taken out of your deck unlike the Hunter card tracking.

<a class="embedly-card" href="https://twitter.com/bdbrode/status/666359351980920832">Ben Brode on Twitter</a>
<script async src="//cdn.embedly.com/widgets/platform.js" charset="UTF-8"></script>

<p>In order to properly explore the probabilities of drawing the cards you are looking for using Discover we will use the following formula(a Hypergeometric Distribution):</p>
> <img src="/images/hypergeomdist.jpg"> where
>
> <b>k</b> is the number of "successes" in the population (This is the amount of a type of card in the sample for example 5 legendaries out of 300 choices)
>
> <b>x</b> is the number of "successes" in the sample (This is the amount of cards of a particular displayed each time discover is used out of the 3 that are presented)
>
> <b>N</b> is the size of the population (This will be the total number of cards that we are choosing from)
>
> <b>n</b> is the number sampled (As the discover mechanic always gives you 3 options this will be 3 in all situations for us)
>
> <b>p</b> is the probability of obtaining exactly x successes (This will be the probability of getting the choice of x number of cards that meet the criteria)
>
> <b><sub>k</sub>C<sub>x</sub></b> is the number of combinations of k things taken x at a time



<p>Now that we know all the rules surrounding Discover lets take a look at each of the cards. (Click each card name to reveal its stats)</p>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingOne">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseOne" aria-expanded="false" aria-controls="collapseOne">
        Sir Finley Mrrgglton
      </a>
    </h4>
  </div>
  <div id="collapseOne" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingOne">
    <div class="panel-body">
      <div class="col-md-3">
        <img src="/images/sir-finley-mrrgglton.gif" />
      </div>
      <div class="col-md-9">
        <p>Sir Finley Mrrgglton is the simplest Discover mechanic in all of Hearthstone to understand. But how do his statistics match up to your expectatoins?</p>
        <p>Sir Finley simply provides you with 3 new basic Hero power options to choose from each of them are listed below:</p>
        <video class="hscard-video" autoplay="autoplay" loop="loop" width="286" height="395" style="top: 0; left: 0; background: rgba(0, 0, 0, 0) no-repeat 0 0; -webkit-background-size: cover; -moz-background-size: cover; -o-background-size: cover; background-size: cover;" data-href="/cards/185-shapeshift#gold" data-usegold="True" data-useanimation="True" data-usevideo="True" data-usegif="True" data-animationurl="http://media-Hearth.cursecdn.com/goldCards/0/185/185.webm" data-gifurl="http://media-Hearth.cursecdn.com/avatars/126/623/185.png" data-goldurl="http://media-Hearth.cursecdn.com/avatars/126/623/185.png" data-imageurl="http://media-Hearth.cursecdn.com/avatars/126/621/185.png" data-width="286">
            <source src="/images/shapeshift.webm" type="video/webm">
        </video>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingTwo">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
        Arch-Thief Rafaam
      </a>
    </h4>
  </div>
  <div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
    <div class="panel-body">
    <img src="/images/arch-thief-rafaam.gif" />
      Arch-Thief Rafaam is the only discover card that doesn't follow the majority of the general Discover rules...
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingThree">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
        Raven Idol
      </a>
    </h4>
  </div>
  <div id="collapseThree" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingThree">
    <div class="panel-body">
      <div class="col-md-3">
        <img src="/images/raven-idol.gif">
      </div>
      <div class="col-md-9">
        <p>The Raven Idol is probably one of the most complex Discover mechanics in the entire game by allowing a Druid or a player that has gained a copy of this card through other methods access to nearly any card in the game that is legal for their class.</p>
        <p>For the sake of simplicty this analysis will assume that the player of the card is a Druid. I will release a calculator at a later date for other classes if they get this spell through Cho/Thought Steal/Nefarian etc.</p>
        <p>Things to note about this card. </p>
        <ul>
          <li>You first have the choice between a spell OR a minion not both! So you have to choose wisely in order to gain an advantage off this card.</li>
          <li>Selecting the spell option limits you as stated above to class spells.</li>
          <li>Selecting the minion option allows choices between both neutral and class minions</li>
          <li>There are currently 26 spell options to choose from.</li>
          <li>There are currently 331 minion options to choose from.</li>
          <li>Of the 331 minion options, there are only 67 Legendaries to choose from.</li>
          <li>Of the 331 minion options, there are only 33 Epics to choose from.</li>
          <li>Of the 331 minion options, there are only 74 Rares to choose from.</li>
          <li>Of the 331 minion options, there are only 157 Commons to choose from.</li>
          <li>Of the 331 minion options, there are only 21 are Druid class minions, which are 4 times more likely to be discovered</li>
        </ul>

        <div>In terms of our formula above we can subsitute in our values about Raven Idol to get a close look at the likelyhood of getting getting the cards you are looking for; for those mathematically inclined read along below, anyone else feel free to skip past it to find out the results.</div>
        <div>One thing to note is that with the Class minions being 4 times more likely to be discovered we have to allow for that in our calculations. I will be taking the route of multiplying those card numbers by 4 just to keep this as simple as possible.</div>
        <hr/>
        <div>
          <h3>Chance of getting x number of Legendary minions presented.</h3>
          <div>Out of the 67 possibilties of Legendary minions there are 3 Druid class minions making the total Legendary count 76.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <blockquote>
            <div><b>k</b> = 76 (there are 76 possible Legendary possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Legendary</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Legendaries presented: 53.9847%</div>
            <div>Chance to get exactly 1 Legendaries presented: 37.0616%</div>
            <div>Chance to get exactly 2 Legendaries presented: 8.3389%</div>
            <div>Chance to get exactly 3 Legendaries presented: 0.6148%</div>
          </blockquote>
        </div>
        <hr/>
         <div>
          <h3>Chance of getting x number of Epic minions presented.</h3>
          <div>Out of the 33 possibilties of Epic minions there are 2 Druid class minions making the total Epic count 38.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <blockquote>
            <div><b>k</b> = 38 (there are 38 possible Epic possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Epic</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Epics presented: 73.7067%</div>
            <div>Chance to get exactly 1 Epics presented: 23.7360%</div>
            <div>Chance to get exactly 2 Epics presented: 2.4739%</div>
            <div>Chance to get exactly 3 Epics presented: 0.0834%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting x number of Rare minions presented.</h3>
          <div>Out of the 74 possibilties of Rare minions there are 8 Druid class minions making the total Rare count 98.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <blockquote>
            <div><b>k</b> = 98 (there are 98 possible Rare possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Rare</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Rares presented: 42.2947%</div>
            <div>Chance to get exactly 1 Rares presented: 42.2947%</div>
            <div>Chance to get exactly 2 Rares presented: 13.9071%</div>
            <div>Chance to get exactly 3 Rares presented: 1.5035%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting x number of Common minions presented.</h3>
          <div>Out of the 157 possibilties of Common minions there are 8 Druid class minions making the total Common count 181.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <blockquote>
            <div><b>k</b> = 181 (there are 181 possible Common possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Common</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Commons presented: 15.6972%</div>
            <div>Chance to get exactly 1 Commons presented: 40.3962%</div>
            <div>Chance to get exactly 2 Commons presented: 34.2987%</div>
            <div>Chance to get exactly 3 Commons presented: 9.6079%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting x number of Taunt minions presented.</h3>
          <div>Out of the 28 possibilties of Taunt minions there are 6 Druid class minions making the total Taunt count 46.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <blockquote>
            <div><b>k</b> = 46 (there are 46 possible Taunt possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Taunt</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Taunts presented: 69.1113%</div>
            <div>Chance to get exactly 1 Taunts presented: 27.2496%</div>
            <div>Chance to get exactly 2 Taunts presented: 3.4935%</div>
            <div>Chance to get exactly 3 Taunts presented: 0.1456%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting that ESPORTS moment (The 1 exact card you need to save yourself).</h3>
          <div>As we have done thus far we will be allowing 4 copies of each Druid minion to be part of the ESPORTS moment calculations.</div>
          <div>Out of the 331 possibilities of minions to be presented 21 are Druid class minions making the total minion count 394.</div>
          <div>An ESPORTS moment where you need exactly a specific Druid minion would have 4 chances out of 394 cards.</div>
          <div>An ESPORTS moment where you need exactly a specific non-Druid minion would have 1 chance out of 394 cards</div>
          <div>Even with a 4 weighting you can only get presented with the card once! Not 3 times.</div>
          <blockquote>
            <div><b>k</b> = 4 (there are 4 possible chances of getting exactly 1 Druid minion possibilities from Raven Idol)</div>
            <div><b>x</b> = Can be 0 or 1 as you either get the card or you dont!</div>
            <div><b>N</b> = There are 394 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 of the Druid card you need for the ESPORTS moment presented: 97.0077%</div>
            <div>Chance to get exactly 1 of the Druid card you need for the ESPORTS moment presented: 2.9696%</div>
            <div>Chance to get exactly 0 of the non-Druid card you need for the ESPORTS moment presented: 99.2462%</div>
            <div>Chance to get exactly 1 of the non-Druid card you need for the ESPORTS moment presented: 0.7538%</div>
          </blockquote>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFour">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseFour" aria-expanded="false" aria-controls="collapseFour">
        Museum Curator
      </a>
    </h4>
  </div>
  <div id="collapseFour" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFour">
    <div class="panel-body">
      <div class="col-md-3">
        <img src="/images/museum-curator.gif">
      </div>
      <div class="col-md-9">
        <p>The Museum Curator is one of the more straight forward Discover mechanics in the game.
          It allows a Priest or a player that has gained a copy of this card through other methods access to all class and neutral Deathrattle minions.</p>
        <p>For the sake of simplicty this analysis will assume that the player of the card is a Priest. I will release a calculator at a later date for other classes if they get this card through Cho/Thought Steal/Nefarian etc.</p>
        <p>Things to note about this card.</p>
        <ul>
          <li>There are currently 32 minions to choose from.</li>
          <li>Of the 32 minion options, there are only 11 Legendaries.</li>
          <li>Of the 32 minion options, there is only 1 Epic.</li>
          <li>Of the 32 minion options, there are only 5 Rares.</li>
          <li>Of the 32 minion options, there are only 15 Commons.</li>
          <li>Of the 32 minion options, there is only 1 Priest class card.</li>
          <li>Of the 32 minion options, there are only 5 taunts.</li>
        </ul>
        <p>In terms of our formula above we can subsitute in our values about Museum Curator to get a close look at the likelyhood of getting the cards you are looking for;
        for those mathematically inclined read along below. anyone else feel free to skip past it to find out the results.</p>
        <p>One thing to note is that with the Class minions being 4 times more likely to be discovered we have to allow for that in our calculations. I will be taking the route of multiplying those card numbers by 4 just to keep things as simple as possible.</p>
        <hr/>
        <div>
          <h3>Chance of getting x number of Legendary minions presented.</h3>
          <div>Out of the 11 possibilties of Legendary minions there are 0 Priest class minions making the total Legendary count 11.</div>
          <div>Out of the 32 possibilities of minions to be presented 1 is a Priest class minions making the total minion count 35.</div>
          <blockquote>
            <div><b>k</b> = 11 (there are 11 possible Legendary possibilities from Museum Curator)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Legendary</div>
            <div><b>N</b> = There are 35 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Legendaries presented: 30.9244%</div>
            <div>Chance to get exactly 1 Legendaries presented: 46.3866%</div>
            <div>Chance to get exactly 2 Legendaries presented: 20.1681%</div>
            <div>Chance to get exactly 3 Legendaries presented: 2.5210%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting x number of Taunt minions presented.</h3>
          <div>Out of the 5 possibilties of Taunt minions there are 0 Priest class minions making the total Taunt count 11.</div>
          <div>Out of the 32 possibilities of minions to be presented 1 is a Priest class minions making the total minion count 35.</div>
          <blockquote>
            <div><b>k</b> = 5 (there are 5 possible Taunt possibilities from Museum Curator)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Taunt</div>
            <div><b>N</b> = There are 35 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Taunts presented: 62.0321%</div>
            <div>Chance to get exactly 1 Taunt presented: 33.2315%</div>
            <div>Chance to get exactly 2 Taunts presented: 4.5837%</div>
            <div>Chance to get exactly 3 Taunts presented: 0.1528%</div>
          </blockquote>
        </div>
        <hr/>
        <div>
          <h3>Chance of getting that ESPORTS moment (The 1 exact card you need to save yourself).</h3>
          <div>As we have done thus far we will be allowing 4 copies of each Priest minion to be part of the ESPORTS moment calculations.</div>
          <div>Out of the 32 possibilities of minions to be presented 1 is a Priest class minions making the total minion count 35.</div>
          <div>An ESPORTS moment where you need exactly a specific Priest minion would have 4 chances out of 35 cards.</div>
          <div>An ESPORTS moment where you need exactly a specific non-Druid minion would have 1 chance out of 35 cards</div>
          <div>Even with a 4 weighting you can only get presented with the card once! Not 3 times.</div>
          <blockquote>
            <div><b>k</b> = 1 (there are 1 possible chances of getting exactly 1 Priest minion possibilities from Museum Curator)</div>
            <div><b>x</b> = Can be 0 or 1 as you either get the card or you dont!</div>
            <div><b>N</b> = There are 35 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 of the Priest card you need for the ESPORTS moment presented: 71.5814%</div>
            <div>Chance to get exactly 1 of the Priest card you need for the ESPORTS moment presented: 28.4186%</div>
            <div>Chance to get exactly 0 of the non-Priest card you need for the ESPORTS moment presented: 91.4286%</div>
            <div>Chance to get exactly 1 of the non-Priest card you need for the ESPORTS moment presented: 8.5714%</div>
          </blockquote>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFive">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseFive" aria-expanded="false" aria-controls="collapseFive">
        Dark Peddler
      </a>
    </h4>
  </div>
  <div id="collapseFive" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFive">
    <div class="panel-body">
      <div class="col-md-3">
        <img src="/images/dark-peddler.gif">
      </div>
      <div class="col-md-9">
        <p>The Dark Peddler is one of the more straight forward Discover mechanics in the game although does have some complexity by allowing both spells or minions to be discovered.
          It allows a Warlock or a player that has gained a copy of this card through other methods access to all class and neutral 1 cost minions and spells.</p>
        <p>For the sake of simplicty this analysis will assume that the player of the card is a Warlock. I will release a calculator at a later date for other classes if they get this card through Cho/Thought Steal/Nefarian etc.</p>
        <p>Things to note about this card.</p>
        <ul>
          <li>There are currently 38 cards to choose from.</li>
          <li>Of the 38 options, there are only 1 Legendaries.</li>
          <li>Of the 38 options, there is only 1 Epic.</li>
          <li>Of the 38 options, there are only 9 Rares.</li>
          <li>Of the 38 options, there are only 27 Commons.</li>
          <li>Of the 38 options, there are only 8 Warlock class cards.</li>
          <li>Of the 38 options, there are only 4 taunts.</li>
          <li>Of the 38 options, there are only 4 spells.</li>
        </ul>
        <p>In terms of our formula above we can subsitute in our values about Museum Curator to get a close look at the likelyhood of getting the cards you are looking for;
        for those mathematically inclined read along below. anyone else feel free to skip past it to find out the results.</p>
        <p>One thing to note is that with the Class minions being 4 times more likely to be discovered we have to allow for that in our calculations. I will be taking the route of multiplying those card numbers by 4 just to keep things as simple as possible.</p>
        <hr/>
        <div>
          <h3>Chance of getting x number of Taunt minions presented.</h3>
          <div>Out of the 4 possibilties of Taunt minions there are 1 Warlock class minions making the total Taunt count 7.</div>
          <div>Out of the 38 possibilities of cards to be presented 8 are Warlock class cards making the total card count 62.</div>
          <blockquote>
            <div><b>k</b> = 4 (there are 4 possible Taunt possibilities from Dark Peddler)</div>
            <div><b>x</b> = Can be 0,1,2 or 3 this is the amount of cards presented that ARE Taunt</div>
            <div><b>N</b> = There are 62 total possible cards</div>
            <div><b>n</b> = 3 (Discover presents 3 options)</div>
          </blockquote>
          <div>Putting these values into our formula above we can establish the following probabilities (rounded to 4 decimal places):</div>
          <blockquote>
            <div>Chance to get exactly 0 Taunts presented: 69.3681%</div>
            <div>Chance to get exactly 1 Taunt presented: 27.4855%</div>
            <div>Chance to get exactly 2 Taunts presented: 3.0539%</div>
            <div>Chance to get exactly 3 Taunts presented: 0.0925%</div>
          </blockquote>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSix">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseSix" aria-expanded="false" aria-controls="collapseSix">
        Jeweled Scarab
      </a>
    </h4>
  </div>
  <div id="collapseSix" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSix">
    <div class="panel-body">
    <img src="/images/jeweled-scarab.gif">
      Jeweled Scarab stuff here
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSeven">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseSeven" aria-expanded="false" aria-controls="collapseSeven">
        Tomb Spider
      </a>
    </h4>
  </div>
  <div id="collapseSeven" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSeven">
    <div class="panel-body">
    <img src="/images/tomb-spider.gif">
       Tomb Spider stuff here
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingEight">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseEight" aria-expanded="false" aria-controls="collapseEight">
        Gorillabot A-3
      </a>
    </h4>
  </div>
  <div id="collapseEight" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingEight">
    <div class="panel-body">
    <img src="/images/gorillabot-a-3.gif">
       Gorillabot A-3 stuff here
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingNine">
    <h4 class="panel-title">
      <a class="collapsed" role="button" data-toggle="collapse" href="#collapseNine" aria-expanded="false" aria-controls="collapseNine">
        Ethereal Conjurer
      </a>
    </h4>
  </div>
  <div id="collapseNine" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingNine">
    <div class="panel-body">
    <img src="/images/ethereal-conjurer.gif">
      Ethereal Conjurer stuff here
    </div>
  </div>
</div>
To be continued
