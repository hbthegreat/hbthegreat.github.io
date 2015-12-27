---
layout: post
title: "CodinGame Solutions"
date: "2015-12-27"
categories: programming
parent-category: Programming
parent-category-link: programming
---
These are my current solutions of CodinGame challenges that I have completed. Will update progressively whenever I have additional time to do more challenges over on <a href="http://www.codingame.com">http://www.codingame.com</a>.
<p>The total amount of challenges I have solved on CodinGame can be seen over on my <a href="https://www.codingame.com/profile/aa91007139792b5a4bdd56bbb5d1a4f0037567">CodinGame Profile</a></p>

The solutions below currently use C# although I look to recomplete them with many other languages in the future.
All of the challenges are over on my github repo of <a href="https://github.com/hbthegreat/CodinGame-Solutions">CodinGame-Solutions</a> although for the time being I will also put the code here.

_**Disclaimer**: These are actual solutions to some of the problems on CodinGame so if you wish to solve the questions yourself then you should probably stop reading to avoid ruining it for yourself!._

## List of Challenges

### Easy Challenges

<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingOne">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseOne" aria-expanded="false" aria-controls="collapseOne">
        Power of Thor
      </a>
    </h4>
  </div>
  <div id="collapseOne" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingOne">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 * ---
 * Hint: You can use the debug stream to print initialTX and initialTY, if Thor seems not follow your orders.
 **/
class Player
{
    static void Main(string[] args)
    {
        string[] inputs = Console.ReadLine().Split(' ');
        int lightX = int.Parse(inputs[0]); // the X position of the light of power
        int lightY = int.Parse(inputs[1]); // the Y position of the light of power
        int initialTX = int.Parse(inputs[2]); // Thor's starting X position
        int initialTY = int.Parse(inputs[3]); // Thor's starting Y position

        var thorX = initialTX;
        var thorY = initialTY;
        // game loop
        while (true)
        {
            int remainingTurns = int.Parse(Console.ReadLine()); // The remaining amount of turns Thor can move. Do not remove this line.
            string directionX = "";
            string directionY = "";
            if(thorX > lightX)
            {
                directionX = "W";
                thorX = thorX - 1;
            } else if(thorX < lightX){
                directionX = "E";
                thorX = thorX + 1;

            }else{
                directionX ="";
            }
            if(thorY > lightY){
                directionY = "N";
                thorY = thorY - 1;
            }else if(thorY < lightY){
                directionY ="S";
                thorY = thorY + 1;
            }else{
                directionY="";
            }
            // Write an action using Console.WriteLine()
            // To debug: Console.Error.WriteLine("Debug messages...");

            Console.WriteLine(directionY+""+directionX); // A single line providing the move to be made: N NE E SE S SW W or NW
        }
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingTwo">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
        The Descent
      </a>
    </h4>
  </div>
  <div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Player
{
    static void Main(string[] args)
    {

        // game loop
        while (true)
        {
            string[] inputs = Console.ReadLine().Split(' ');
            int SX = int.Parse(inputs[0]);
            int SY = int.Parse(inputs[1]);
            var currentHeighestMountain = 10;
            var currentHeighestHeight = 0;
            var order = "empty";
            for (int i = 0; i < 8; i++)
            {
                int MH = int.Parse(Console.ReadLine()); // represents the height of one mountain, from 9 to 0. Mountain heights are provided from left to right.
                if(MH > currentHeighestHeight){
                    currentHeighestHeight =MH;
                    currentHeighestMountain = i;
                }
                if(currentHeighestMountain == SX){
                    order ="FIRE";
                }
                else{
                    order ="HOLD";
                }
            }
            Console.WriteLine(order); // either:  FIRE (ship is firing its phase cannons) or HOLD (ship is not firing).
            // Write an action using Console.WriteLine()
            // To debug: Console.Error.WriteLine("Debug messages...");
        }
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingThree">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
        Skynet: The Chasm
      </a>
    </h4>
  </div>
  <div id="collapseThree" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingThree">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Player
{
    static void Main(string[] args)
    {
        int road = int.Parse(Console.ReadLine()); // the length of the road before the gap.
        int gap = int.Parse(Console.ReadLine()); // the length of the gap.
        int platform = int.Parse(Console.ReadLine()); // the length of the landing platform.

        // game loop
        while (true)
        {
            int speed = int.Parse(Console.ReadLine()); // the motorbike's speed.
            int coordX = int.Parse(Console.ReadLine()); // the position on the road of the motorbike.

            var command = "";
            if(coordX == road - 1){
                command = "JUMP";
            }else if(coordX < road + gap){
                //Setting speed if needed
                if(speed < gap+1){
                    command = "SPEED";
                }else if(speed > gap+1){
                    command = "SLOW";
                }
                else{
                    command = "WAIT";
                }

            } else{
                command = "SLOW";
            }



            // Write an action using Console.WriteLine()
            // To debug: Console.Error.WriteLine("Debug messages...");

            Console.WriteLine(command); // A single line containing one of 4 keywords: SPEED, SLOW, JUMP, WAIT.
        }
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFour">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseFour" aria-expanded="false" aria-controls="collapseFour">
        Temperatures
      </a>
    </h4>
  </div>
  <div id="collapseFour" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFour">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        int N = int.Parse(Console.ReadLine()); // the number of temperatures to analyse
        string TEMPS = Console.ReadLine(); // the N temperatures expressed as integers ranging from -273 to 5526

        var result = "";
        if(N == 0){
            result = "0";
        }else{
            string[] TEMPSSPLIT = TEMPS.Split(' ');
            var closest = Convert.ToInt32(TEMPSSPLIT[0]);
            for(int i =0; i<N; i++){
                if(Math.Abs(Convert.ToInt32(TEMPSSPLIT[i])) < Math.Abs(closest))
                {
                    closest = Convert.ToInt32(TEMPSSPLIT[i]);
                }else if(Math.Abs(Convert.ToInt32(TEMPSSPLIT[i]))==Math.Abs(closest))
                {
                    if(closest<Convert.ToInt32(TEMPSSPLIT[i]))
                    {
                        closest = Convert.ToInt32(TEMPSSPLIT[i]);
                    }
                }
            }
            result = closest+"";
        }

        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");

        Console.WriteLine(result);
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingFive">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseFive" aria-expanded="false" aria-controls="collapseFive">
        Mars Lander - Level 1
      </a>
    </h4>
  </div>
  <div id="collapseFive" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingFive">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Player
{
    static void Main(string[] args)
    {
        string[] inputs;
        int surfaceN = int.Parse(Console.ReadLine()); // the number of points used to draw the surface of Mars.
        for (int i = 0; i < surfaceN; i++)
        {
            inputs = Console.ReadLine().Split(' ');
            int landX = int.Parse(inputs[0]); // X coordinate of a surface point. (0 to 6999)
            int landY = int.Parse(inputs[1]); // Y coordinate of a surface point. By linking all the points together in a sequential fashion, you form the surface of Mars.
        }

        // game loop
        while (true)
        {
            inputs = Console.ReadLine().Split(' ');
            int X = int.Parse(inputs[0]);
            int Y = int.Parse(inputs[1]);
            int hSpeed = int.Parse(inputs[2]); // the horizontal speed (in m/s), can be negative.
            int vSpeed = int.Parse(inputs[3]); // the vertical speed (in m/s), can be negative.
            int fuel = int.Parse(inputs[4]); // the quantity of remaining fuel in liters.
            int rotate = int.Parse(inputs[5]); // the rotation angle in degrees (-90 to 90).
            int power = int.Parse(inputs[6]); // the thrust power (0 to 4).

            var newPower = power;
            if(vSpeed < -40){
                newPower = 4;
            } else if(vSpeed > -40){
                newPower = 0;
            }else {
                newPower = power;
            }
            // Write an action using Console.WriteLine()
            // To debug: Console.Error.WriteLine("Debug messages...");

            Console.WriteLine("0 "+newPower); // 2 integers: rotate power. rotate is the desired rotation angle (should be 0 for level 1), power is the desired thrust power (0 to 4).
        }
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSix">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseSix" aria-expanded="false" aria-controls="collapseSix">
        ASCII Art
      </a>
    </h4>
  </div>
  <div id="collapseSix" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSix">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        int L = int.Parse(Console.ReadLine());
        int H = int.Parse(Console.ReadLine());
        string T = Console.ReadLine();
        List<string> Lines = new List<string>();
        for (int i = 0; i < H; i++)
        {
            string ROW = Console.ReadLine();
            Lines.Add(ROW);
        }

        var standardInput = T.ToUpper();
        var outputString = "";
        foreach(var line in Lines){
            for(int i = 0; i < standardInput.Length; i++){

                if(standardInput[i] > 64 && standardInput[i] < 91){
                    var spot = (standardInput[i]-65)*L;
                    outputString = outputString + line.Substring(spot,L);
                }
                else{
                    outputString = outputString + line.Substring(L*26,L);
                }
            }
            outputString = outputString + "\n";
        }




        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");

        Console.WriteLine(outputString);
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingSeven">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseSeven" aria-expanded="false" aria-controls="collapseSeven">
        Chuck Norris
      </a>
    </h4>
  </div>
  <div id="collapseSeven" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingSeven">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        string MESSAGE = Console.ReadLine();

        var messageAsBinaryString = ToBinary(ConvertToByteArray(MESSAGE, Encoding.UTF8));

        var messageAsChuckNorris = ToChuckNorris(messageAsBinaryString);
        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");
       //Console.WriteLine(messageAsBinaryString);
        Console.WriteLine(messageAsChuckNorris);
    }

    public static byte[] ConvertToByteArray(string str, Encoding encoding)
    {
        return encoding.GetBytes(str);
    }

    public static String ToBinary(Byte[] data)
    {
        return string.Join("", data.Select(theByte => Convert.ToString(theByte, 2).PadLeft(7,'0')));
    }

    public static String ToChuckNorris(string binaryString)
    {
        var chuckNorris = "";

        int count = 0;
        int prev = '2';

        //character = 1
        foreach (char character in  binaryString.ToCharArray()) {
            if (character != prev) {
                for (int j = 0 ; j < count ; j++)
                {
                    chuckNorris = chuckNorris + "0";
                }
                if (count != 0)
                {
                    chuckNorris = chuckNorris + " ";
                }
                chuckNorris = chuckNorris + ((character == '0') ? "00 " : "0 ");
                count = 1;
            } else {
                count++;
            }
            prev = character;
        }
        for (int j = 0 ; j < count ; j++){
            chuckNorris = chuckNorris+"0";
        }
        return chuckNorris;
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingEight">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseEight" aria-expanded="false" aria-controls="collapseEight">
        MIME Type
      </a>
    </h4>
  </div>
  <div id="collapseEight" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingEight">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        int N = int.Parse(Console.ReadLine()); // Number of elements which make up the association table.
        int Q = int.Parse(Console.ReadLine()); // Number Q of file names to be analyzed.
        List<string> files = new List<string>();
        Dictionary<string,string> mimeTypes = new Dictionary<string,string>();
        for (int i = 0; i < N; i++)
        {
            string[] inputs = Console.ReadLine().Split(' ');
            string EXT = inputs[0]; // file extension
            string MT = inputs[1]; // MIME type.
            mimeTypes.Add(EXT.ToLower(),MT);
        }
        for (int i = 0; i < Q; i++)
        {
            string FNAME = Console.ReadLine(); // One file name per line.
            files.Add(FNAME);
        }

        foreach(string file in files){
            var dotPosition = file.LastIndexOf(".");
            var extension = file.Substring(dotPosition+1).ToLower();

            if(dotPosition == -1){
                Console.WriteLine("UNKNOWN");
            }
            else{
                if(mimeTypes.ContainsKey(extension)){
                    Console.WriteLine(mimeTypes.FirstOrDefault(x => x.Key == extension).Value);
                }else
                {
                    Console.WriteLine("UNKNOWN");
                }
            }
        }

        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");

        //Console.WriteLine("UNKNOWN"); // For each of the Q filenames, display on a line the corresponding MIME type. If there is no corresponding type, then display UNKNOWN.
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingNine">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseNine" aria-expanded="false" aria-controls="collapseNine">
        Defibrillators
      </a>
    </h4>
  </div>
  <div id="collapseNine" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingNine">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;
using System.Globalization;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        string LON = Console.ReadLine();
        string LAT = Console.ReadLine();
        int N = int.Parse(Console.ReadLine());
        List<string> DEFIBs = new List<string>();
        for (int i = 0; i < N; i++)
        {
            string DEFIB = Console.ReadLine();
            DEFIBs.Add(DEFIB);
        }

        var baseDistance = double.PositiveInfinity;
        var centreName = "";

        foreach(var defib in DEFIBs){
            var data = defib.Split(';');
            var nameOfCentre = data[1];
            var lng = float.Parse(data[4].Replace(',','.'), CultureInfo.InvariantCulture.NumberFormat);
            var lat = float.Parse(data[5].Replace(',','.'), CultureInfo.InvariantCulture.NumberFormat);
            var userLng = float.Parse(LON.Replace(',','.'), CultureInfo.InvariantCulture.NumberFormat);
            var userLat =float.Parse(LAT.Replace(',','.'), CultureInfo.InvariantCulture.NumberFormat);

            //Formulas
            var x = (userLng-lng) * Math.Cos((lat + userLat)/2);
            var y = (userLat-lat);
            var d = Math.Sqrt(x*x+y*y) * 6371;

            if(d < baseDistance){
                baseDistance = d;
                centreName = nameOfCentre;
            }
        }
        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");

        Console.WriteLine(centreName);
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>
<div class="panel panel-default">
  <div class="panel-heading" role="tab" id="headingTen">
    <h4 class="panel-title">
      <a role="button" data-toggle="collapse" href="#collapseTen" aria-expanded="false" aria-controls="collapseTen">
        Horse-racing Duals
      </a>
    </h4>
  </div>
  <div id="collapseTen" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTen">
    <div class="panel-body">
      <div class="solution">
{% highlight csharp %}
using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        int N = int.Parse(Console.ReadLine());
        List<int> powerLevels = new List<int>();
        for (int i = 0; i < N; i++)
        {
            int pi = int.Parse(Console.ReadLine());
            powerLevels.Add(pi);
        }

        var minDiff = 10000000;
        powerLevels = powerLevels.OrderBy(x => x).ToList();
        for(int i = 0; i< powerLevels.Count() - 1; i++)
        {
            var diff = Math.Abs(powerLevels[i]- powerLevels[i+1]);
            if(diff < minDiff){
                minDiff = diff;
            }

            if (minDiff == 1)
            {
                break;
            }
        }
        // Write an action using Console.WriteLine()
        // To debug: Console.Error.WriteLine("Debug messages...");

        Console.WriteLine(minDiff);
    }
}
{% endhighlight%}
      </div>
    </div>
  </div>
</div>

### Medium Challenges
1. Coming soon

### Hard Challenges
1. Coming soon

### Very Hard Challenges
1. Coming soon
