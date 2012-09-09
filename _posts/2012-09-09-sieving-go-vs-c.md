---
layout: post
title: "Sieving: Go vs C"
tags: english 
---

Last year, for my Mastermath course [Parallel Algorithms](http://www.staff.science.uu.nl/~bisse101/Education/PA/pa.html), I had to implement a sequential version of the famous Erathostenes' Sieve in C.

Recently I got interested in the [Go Programming language](http://golang.org), so I thought that implementing the same version of the Sieve (same operations, in the same order, even though probably it's not the most efficient implementation you can find) would have been a nice exercise, both for learning Go and for measuring its capabilities.

So, after having pleasantly discovered that Go can definitely be more compact than C, I looked for the number of primes below 100 millions and 1 billion, measuring the time (using the Linux command `time`) it took for both the implementations to find the result.

For the C Language, I run the tests for the non-optimized (i.e. -O0) and the higly optimized version (i.e. -O3) of the program, which I will denote respectively as C and C3.

Since I ran all the experiments not on a dedicated pc but on my laptop, a Intel Core i5 520M @ 2.40Ghz, 6Gb RAM, WD Caviar Black 500Gb 7200rpm, running Ubuntu 12.04 64bit, which was not a noise-free environment (I was using it in the meantime, so there were some programs running), I ran those experiments 20+ times (especially for the 1 billion case, since it roughly takes 20 seconds for the programs to finish, leaving space for a lot of interference) and took the best results.

You can find the source code of the C implementation in [seq.c](https://github.com/Heliosmaster/BSPErathostenes/blob/master/seq.c) and [seqSieve.c](https://github.com/Heliosmaster/BSPErathostenes/blob/master/seqSieve.c) (with the actual computations), while the Go version can be found in [simple_sieve.go](http://gist.github.com/3677584).

The data obtained is the following:

### 10<sup>8</sup>

- C: 2.78 s
- C3: 1.71 s
- Go: 1.98 s

###10<sup>9</sup>

- C: 26.15 s
- C3: 20.01 s
- Go: 19.87 s

Which can be prettily organized as the following bar graph:

<script type="text/javascript" src="https://www.google.com/jsapi"></script>
<script type="text/javascript">
      google.load("visualization", "1", {packages:["corechart"]});
      google.setOnLoadCallback(drawChart);
      function drawChart() {
        var data = google.visualization.arrayToDataTable([
          ['', 'C', 'C3', 'Go'],
          ['10^8', 2.78, 1.71, 1.98],
	  ['10^9', 26.15, 20.01, 19.87],
        ]);

        var options = {
          title: 'C vs. Go',
	  colors: ['#EC5536','#2B63DA','#50C41E'],
          hAxis: {title: 'Time (in seconds) to find the correct number of primes below the threshold'} 
        };

        var chart = new google.visualization.BarChart(document.getElementById('chart_div'));
        chart.draw(data, options);
      }
</script>

<div id="chart_div" style="width: 800px; height: 300px;margin-bottom:10px"></div>

Clearly (and surprisingly), the performance of the Go programming language can be compared to one of C with the highest level of optimization, even beating it for the 10<sup>9</sup> case.

Last year I was able to speed up considerably the generation of primes by splitting the computation among a good amount of processors, using [BSPonMPI](https://github.com/BSPWorldwide/BSPonMPI). Will we be able to get a similar boost in performance using parallelism with Go? If yes, to what extent?

This is definitely worth a deeper investigation.
