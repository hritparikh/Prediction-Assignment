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

df_testing_final[, c(1, 2, 161)]</code></pre>
<pre><code>##     X user_name pred_classe
## 1   1      B
## 2   2      A
## 3   3      B
## 4   4      A
## 5   5      A
## 6   6      E
## 7   7      D
## 8   8      B
## 9   9      A
## 10 10      A
## 11 11      B
## 12 12      C
## 13 13      B
## 14 14      A
## 15 15      E
## 16 16      E
## 17 17      A
## 18 18      B
## 19 19      B
## 20 20      B 
</code></pre>


</div>


