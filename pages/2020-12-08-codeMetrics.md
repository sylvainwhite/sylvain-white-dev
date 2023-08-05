---
layout: misc
title: "Code Metrics"
author: "Sylvain White"
categories: subCategory
tags: [quality]
# image: city-2.jpg
---
<br/>

### Code coverage

From the paper [Minimum Acceptable Code Coverage](https://www.bullseye.com/minimum.html){:target="_blank"}

* Code coverage: percentage of the source code executed when a particular test suite runs
* Code coverage of **70-80% is a reasonable goal** for system test 
* Empirical studies found that coverage above 70-80% isn't valuable since:
    * it is time consuming
    * it leads to a relatively slow bug detection rate 
* For Javascript, JEST [[web](https://jestjs.io/){:target="_blank"}] does a great job!

<br/>

### Code metrics

Based on:
* [Code Metrics Values](https://docs.microsoft.com/en-us/visualstudio/code-quality/code-metrics-values?view=vs-2019){:target="_blank"} by Microsoft
* [Deciding on Metrics]({{ site.github.url }}/resources/decidingOnMetrics.jpg "Deciding on Metrics"){:target="_blank"} by Andrew Binstock, SD Times Issue 171

<br/>

#### Visual Studio Code Metrics
* There are tons of metrics but I like the simplicity of the 'Visual Studio Code Metrics'
* Unfortunately, 'Visual Studio Code Metrics' is only available in the .NET framework
* Here is a snapshot of its results:
![]({{ site.github.url }}/resources/visualCodeMetricsAnalysis.jpg "Visual Studio code analysis"){:target="_blank"}
* It has 5 metrics:
    * Maintainability index 
    * Cyclomatic Complexity
    * Depth of Inheritance 
    * Class Coupling 
    * Lines of Source code 
* Note on 'Maintainability index'
    * This metrics is based on:
        * cyclomatic complexity
        * Halstead complexity [[web](https://www.verifysoft.com/en_halstead_metrics.html){:target="_blank"}]
        * the size of the codebase
        * the percentage of comment lines  

#### JavaScript
* The tool which is the closest to 'Visual Studio Code Metrics' in JavaScript is 'plato' [[web](https://github.com/es-analysis/plato){:target="_blank"}]
    * View a snapshot of its results [[web](http://es-analysis.github.io/plato/examples/hapi/){:target="_blank"}]
    * It has 3 metrics:
        * Maintainability index
        * Lines of Source code
        * Estimated errors in implementation
    * Note on 'Estimated errors in implementation'
        * 'Estimated errors in implementation' is also known 'Halsteads delivered Bugs' [[web](https://www.verifysoft.com/en_halstead_metrics.html){:target="_blank"}] 
        * It is an estimate for the number of errors that might occur in the implementation
        * It is based on code complexity

<br/>

#### Code metrics - other valuable resources

* [Top Five Code Metrics to Help You Test Better](https://blog.gurock.com/code-metrics-to-test-better/){:target="_blank"}
* [Measure Your Code Using Code Metrics](https://www.c-sharpcorner.com/article/measure-your-code-using-code-metrics/){:target="_blank"}