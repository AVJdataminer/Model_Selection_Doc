# Model_Selection_Doc
This Rmarkdown outlines the important steps in model selection and pre-processing steps in data science and machine learning projects. An example project will be created as well to show the use of the squeaky R package in executing these steps.


<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<meta charset="utf-8" />
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="generator" content="pandoc" />


<meta name="author" content="Aiden V Johnson" />

<meta name="date" content="2017-12-13" />

<title>Model Selection Method</title>

<style type="text/css">code{white-space: pre;}</style>
<style type="text/css">
  pre:not([class]) {
    background-color: white;
  }
</style>
<script type="text/javascript">
if (window.hljs && document.readyState && document.readyState === "complete") {
   window.setTimeout(function() {
      hljs.initHighlighting();
   }, 0);
}
</script>



<style type="text/css">
h1 {
  font-size: 34px;
}
h1.title {
  font-size: 38px;
}
h2 {
  font-size: 30px;
}
h3 {
  font-size: 24px;
}
h4 {
  font-size: 18px;
}
h5 {
  font-size: 16px;
}
h6 {
  font-size: 12px;
}
.table th:not([align]) {
  text-align: left;
}
</style>


</head>

<body>

<style type="text/css">
.main-container {
  max-width: 940px;
  margin-left: auto;
  margin-right: auto;
}
code {
  color: inherit;
  background-color: rgba(0, 0, 0, 0.04);
}
img {
  max-width:100%;
  height: auto;
}
.tabbed-pane {
  padding-top: 12px;
}
button.code-folding-btn:focus {
  outline: none;
}
</style>



<div class="container-fluid main-container">

<!-- tabsets -->
<script>
$(document).ready(function () {
  window.buildTabsets("TOC");
});
</script>

<!-- code folding -->






<div class="fluid-row" id="header">



<h1 class="title toc-ignore">Model Selection Method</h1>
<h4 class="author"><em>Aiden V Johnson</em></h4>
<h4 class="date"><em>12/13/2017</em></h4>

</div>


<div id="problem-identification" class="section level2">
<h2>Problem Identification</h2>
<hr />
<div id="define-the-questiongenerate-a-working-hypothesis." class="section level3">
<h3>Define the question:Generate a working hypothesis.</h3>
<div id="identify-the-modeling-project-goal." class="section level4">
<h4>Identify the modeling project Goal.</h4>
<p>e.g Predict device failures.</p>
</div>
<div id="identify-the-data-needed-and-or-available." class="section level4">
<h4>Identify the data needed and or available.</h4>
<p>e.g Daily aggregated telemetry device failure data.</p>
</div>
<div id="define-the-data-timeframe" class="section level4">
<h4>Define the data Timeframe:</h4>
<p>e.g. 01/01/2015-11/02/2015</p>
</div>
<div id="describe-the-modeling-response" class="section level4">
<h4>Describe the Modeling Response:</h4>
<p>e.g. Binary, 0 or 1, non-failure = 0, failure = 1</p>
</div>
<div id="classification-or-regression-model" class="section level4">
<h4>Classification or Regression Model:</h4>
<p>e.g. Classification</p>
</div>
<div id="what-deliverables-will-be-generated" class="section level4">
<h4>What Deliverables will be generated:</h4>
<p>e.g.PDF outlining modeling process from data exploration to best model results.</p>
<hr />
</div>
</div>
</div>
<div id="begin-exploratory-data-analysis" class="section level2">
<h2>Begin Exploratory Data Analysis</h2>
<div id="build-directories" class="section level3">
<h3>Build Directories</h3>
<ul>
<li>Create a modeling path and output directories to stay organized I created an R package with functions for data pre-processing called Squeaky, as in squeaky clean data. This is still a work in progress butit streamlines my work flow greatly. This package is available on my Github account and can be installed with devtools. Included in this package is a function that creates a timestamped folder of directories for modeling procedures. This allows automated version control and allocates outputs to designated folders which can then be called upon for reporting with easy repeatability.</li>
</ul>
</div>
<div id="review-response-variable-distribution" class="section level3">
<h3>Review Response variable distribution</h3>
<ul>
<li>Does it need to be transformed?</li>
<li>Is it normally distributed?</li>
</ul>
</div>
<div id="review-data-summary-and-data-attributes" class="section level3">
<h3>Review Data Summary and Data Attributes</h3>
<p>Adapt modeling plan as you learn more about the data.</p>
</div>
<div id="review-distribution-boxplots-or-univariate-and-bi-variate-distribution-plots" class="section level3">
<h3>Review Distribution Boxplots or univariate and bi-variate distribution plots</h3>
</div>
<div id="looking-for-collinearity-of-variables" class="section level3">
<h3>Looking for collinearity of variables</h3>
<ul>
<li>Also good to review correlation with response variable.</li>
</ul>
</div>
<div id="consider-applying-unsupervised-for-feature-extraction" class="section level3">
<h3>Consider applying Unsupervised for Feature Extraction</h3>
</div>
<div id="check-for-outliers" class="section level3">
<h3>Check for Outliers</h3>
</div>
<div id="remove-variables-with-near-zero-variance" class="section level3">
<h3>Remove Variables with Near Zero Variance</h3>
</div>
<div id="rescale-and-center-the-data-for-modeling" class="section level3">
<h3>Rescale and Center the Data for Modeling</h3>
</div>
<div id="review-the-data-for-missing-and-na-values." class="section level3">
<h3>Review the Data for Missing and NA values.</h3>
</div>
<div id="find-variables-that-are-100-unique-values" class="section level3">
<h3>Find Variables That are 100% Unique values</h3>
<p>These need to be removed, usually a count or id variable.</p>
</div>
<div id="create-a-test-and-train-group" class="section level3">
<h3>Create a test and train group</h3>
<ul>
<li>Data with no na and near zero variance filtered data</li>
<li>Rename failure to Response</li>
</ul>
<hr />
</div>
</div>
<div id="fit-models" class="section level2">
<h2>Fit models</h2>
<div id="logistic-regression" class="section level3">
<h3>Logistic Regression</h3>
</div>
<div id="area-under-the-curve" class="section level3">
<h3>Area Under the Curve</h3>
</div>
<div id="random-forest-model" class="section level3">
<h3>Random Forest Model</h3>
</div>
<div id="parameter-tuning-with-grid-search-or-random-search-methods" class="section level3">
<h3>parameter tuning with grid search or random search methods</h3>
<div id="model-performance-confusion-matrix" class="section level4">
<h4>Model Performance Confusion Matrix</h4>
<hr />
</div>
</div>
</div>
<div id="model-review-and-refining-process" class="section level2">
<h2>Model Review and Refining process</h2>
</div>




</div>

<script>
// add bootstrap table styles to pandoc tables
function bootstrapStylePandocTables() {
  $('tr.header').parent('thead').parent('table').addClass('table table-condensed');
}
$(document).ready(function () {
  bootstrapStylePandocTables();
});
</script>

<!-- dynamically load mathjax for compatibility with self-contained -->
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>

</body>
</html>
