# Prediction-Assignment
Machine Learning


<div class="fluid-row" id="header">


</div>


<div id="data-analysis" class="section level1">
<h1>Data Analysis</h1>
<div id="we-download-data-to-local-for-analysis" class="section level3">
<h3>We download data to local for analysis</h3>
<pre><code>training &lt;- read.csv(&quot;C:/Users/User/Desktop/pml-training.csv&quot;)
testing &lt;- read.csv(&quot;C:/Users/User/Desktop/pml-testing.csv&quot;)

training &lt;- training[, colSums(is.na(training)) == 0]
testing &lt;- testing[, colSums(is.na(testing)) == 0]

trainData &lt;- training[, -c(1:7)]
testData &lt;- testing[, -c(1:7)]</code></pre>
</div>
<div id="fit-model-and-do-corss-validation" class="section level3">
<h3>fit model and do corss-validation</h3>
<pre><code>library(caret)

fitControl &lt;- trainControl(
  method = &quot;repeatedcv&quot;,
  number = 10,
  repeats = 3,
  classProbs = TRUE
)


set.seed(1)
nbfit &lt;- train(classe~., data = trainData,
               method = &quot;nb&quot;,   
               trControl = fitControl,
               na.action = na.pass
)</code></pre>
</div>
<div id="prediction" class="section level3">
<h3>Prediction</h3>
<pre><code>pred &lt;- predict(nbfit,testData,type=&quot;raw&quot;)</code></pre>
</div>
</div>




</div>


