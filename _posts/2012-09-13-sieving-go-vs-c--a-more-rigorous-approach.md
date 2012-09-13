---
layout: post
title: "Sieving: Go vs C - A more rigorous approach"
tags: english 
---

##Apology of a (soon to be) mathematician

A few days ago I wrote [a post](/2012/09/09/sieving-go-vs-c/) about a performance comparison between Go and C when using Erathostenes' Sieve to find primes. After having (naively) submitted the post at [Hacker News](http://news.ycombinator.com/item?id=4499443), somebody submitted the post on [/r/programming](http://www.reddit.com/r/programming/comments/zpf71/go_vs_c/), where it caused quite a lot of debate.

Most of the comments (I am also considering the ones made directly in this blog) were absolutely correct in criticizing my work. It was definitely not as accurate as I thought. Actually, it was so flawed that it showed **false results**.

Go is not (yet) faster than C.

Somebody correctly suggested that it not entirely correct to talk about speed of programming languages: Go and C are merely language, characterized by words and rules (not differently from italian or english). It's the implementation, or how the programs written in some language are translated in such a way that it can be interpreted and executed by a machine, that makes a difference in speed. Anyway, for sake of simplicity, I will keep on talking about Go vs C, instead of "Go implementation" vs "C implementation"; you know what I am actually talking about.

So, this was the first was the first flaw in my reasoning: I should have specified exactly which implementation of Go and C I was using.

* C: `gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)`
* Go: `go version go1.0.2`

Truth to be told, I have no idea of which implementation of Go I am using: I have a 64-bit OS so I guess I am using the `6g`; anyway, I downloaded and installed the version for amd64 from the Go website.

The second very big flaw in my comparison was on the program itself: **the C version and the Go version were performing different things**. In particular, with C, after sieving, I was creating a new array with just the primes (i.e. no 0s in between); this was the main reason behind the fact that previously Go and C were almost tied: if they had performed the same operations, C would have finished definitely earlier than Go.

In my partial defense on this, I'll say that the original C program was used for something else (namely it was called in a parallel algorithm), and that I definitely needed the bare array of primes.

This was also the reason why I used an array of `ints` instead of using a vector of booleans (as suggested by [julesjacobs](http://www.reddit.com/user/julesjacobs)) in which the number itself is the index of an entry. I also have somewhat of an excuse for this, since previously I just wanted to see their behaviour not with the most efficient implementation of the Erathostenes' Sieve, but the one which I used last year. I admitted that it was definitely not the smartest choice of a program, but it was more to get an idea of their performance.

And lastly, I probably didn't use the correct way of timing, since I outputted the real time and not user time, which as [Killbot3000](http://www.reddit.com/user/Killbot3000) suggests, fluctuates a lot less for longer timings.

**All in all, was there something good about my previous experiments?** The answer is, most likely, **no**.

Since my aspiration is to be a decent mathematician, or at least a decent scientist, I could not avoid repeating the experiments, for sake of truth.

## Go vs C - Part II

The code that I used (along with the results) of these experiments, can be found [here](https://github.com/Heliosmaster/Sieving--Go-vs-C).

1. I fixed the C implementation: now it's on a single file (sorry for not being that good of a programmer, yet) and it does roughly what Go does: array creation, sieving and counting of the primes
2. I used julesjacobs' C++ version that uses a vector of booleans, just to understand how fast would it be.
3. For the timings, I used `time -f "%U %S %e %M"`, so now I have the real time and user time data, along with the memory used.

Since, as I learned, `-O2` is the level of optimization commonly used, I decided to "waste" a little more time and perform the experiments with all the 4 levels of optimization: 0,1,2,3.

In the following graphs

* Go denotes Go (how original)
* Cx denotes my C version (with the array of `int`s), where x=0,1,2,3 denotes the level of optimization.
* Cpx denotes the C++ version with the vector of booleans, where x=1,2,3 denotes the level of optimization (the `-O0` version was a LOT slower than all the others, making the graphs less readable, but the data is still in the repository).

###User time

<script type="text/javascript" src="https://www.google.com/jsapi"></script>
<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
          ['', 'C0', 'C1','C2','C3','Cp1','Cp2','Cp3','Go'],
          ['10^8',  1.89,1.44,1.41,1.4,0.93,0.82,0.82,1.86], 
        ]);

        var options = {
//          title: 'C vs. Go',
//	  colors: ['#EC5536','#2B63DA','#50C41E'],
          hAxis: {title: 'Time (in seconds) to find the correct number of primes below the threshold',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div" style="width: 800px; height: 400px;margin-bottom:10px"></div>

<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
          ['', 'C0', 'C1','C2','C3','Cp1','Cp2','Cp3','Go'],
	  ['10^9', 22.27,17.99,17.47,17.26,13.06,11.37,11.37,19.46],
        ]);

        var options = {
//          title: 'C vs. Go',
//	  colors: ['#EC5536','#2B63DA','#50C41E'],

          hAxis: {title: 'Time (in seconds) to find the correct number of primes below the threshold',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div2'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div2" style="width: 800px; height: 400px;margin-bottom:10px"></div>


###Real time

<script type="text/javascript" src="https://www.google.com/jsapi"></script>
<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
          ['', 'C0', 'C1','C2','C3','Cp1','Cp2','Cp3','Go'],
          ['10^8',2.04,1.56,1.52,1.52,0.94,0.83,0.83,2.05], 
        ]);

        var options = {
//          title: 'C vs. Go',
//	  colors: ['#EC5536','#2B63DA','#50C41E'],
          hAxis: {title: 'Time (in seconds) to find the correct number of primes below the threshold',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div3'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div3" style="width: 800px; height: 400px;margin-bottom:10px"></div>

<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
          ['', 'C0', 'C1','C2','C3','Cp1','Cp2','Cp3','Go'],
	  ['10^9',23.3,18.88,18.43,18.21,13.15,11.45,11.45,20.42],
        ]);

        var options = {
//          title: 'C vs. Go',
//	  colors: ['#EC5536','#2B63DA','#50C41E'],

          hAxis: {title: 'Time (in seconds) to find the correct number of primes below the threshold',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div4'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div4" style="width: 800px; height: 400px;margin-bottom:10px"></div>

### Memory
<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
		['', 'C', 'Cp','go'],
		['10^8',783296,27488,786384],
       ]);

        var options = {
//	  colors: ['#EC5536','#2B63DA','#50C41E'],
          hAxis: {title: 'Memory used (kB)',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div5'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div5" style="width: 800px; height: 200px;margin-bottom:10px"></div>

<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
		['', 'C', 'Cp','go'],
		['10^9',7814544,247136,7831328],
        ]);

        var options = {
//          title: 'C vs. Go',
//	  colors: ['#EC5536','#2B63DA','#50C41E'],

          hAxis: {title: 'Memory used (kB)',minValue:0} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div6'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div6" style="width: 800px; height: 200px;margin-bottom:10px"></div>

## Final remarks

After these experiments, it's more clear that Go has not (yet) a speed comparable with the one of C, which  is more than understandable considering its recent birth. Nonetheless it has some advantages (garbage-collection, etc.) and I would not be surprised if in a few years (after it matures and gets faster) it will get widely used in the scientific community.

We can also see how the algorithm itself is not optimal. The version with the vector of booleans performs much better taking MUCH less space. 

The open question of the previous post still remains valid: how does Go perform with parallelism? Are we able to get decent improvement without adding too much complexity to the code? It definitely is, as I said, a matter worth investigating.
